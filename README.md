# api_final

API для социальной сети Yatube.

## Описание

REST API для проекта Yatube. Позволяет работать с публикациями,
комментариями, сообществами и подписками. Аутентификация — JWT.

## Технологии

- Python 3.11
- Django 3.2.16
- Django REST Framework 3.12.4
- djangorestframework-simplejwt 4.7.2
- django-filter 2.4.0

## Установка

Клонировать репозиторий и перейти в него:

```
git clone git@github.com:pxleblank/api-final-yatube-ad.git
cd api-final-yatube-ad
```

Создать и активировать виртуальное окружение:

```
python -m venv venv
source venv/bin/activate     # Linux / macOS
venv\Scripts\activate        # Windows
```

Установить зависимости:

```
pip install -r requirements.txt
```

Применить миграции:

```
cd yatube_api
python manage.py migrate
```

Запустить сервер:

```
python manage.py runserver
```

## Аутентификация

Для получения JWT-токена отправьте POST-запрос на
`/api/v1/jwt/create/` с полями `username` и `password`.

Полученный `access`-токен передавайте в заголовке:

```
Authorization: Bearer <access>
```

## Основные эндпоинты

- `GET /api/v1/posts/` — список публикаций (доступно без авторизации).
- `POST /api/v1/posts/` — создать публикацию.
- `GET /api/v1/posts/{id}/` — получить публикацию.
- `PUT/PATCH/DELETE /api/v1/posts/{id}/` — изменить или удалить
  (только автор).
- `GET /api/v1/posts/{post_id}/comments/` — список комментариев к посту.
- `POST /api/v1/posts/{post_id}/comments/` — создать комментарий.
- `GET /api/v1/groups/` — список сообществ.
- `GET /api/v1/follow/` — список подписок текущего пользователя.
- `POST /api/v1/follow/` — подписаться на пользователя.

Подробная документация: `/redoc/` после запуска сервера.

## Автор

Иван Олегович (pxleblank).
