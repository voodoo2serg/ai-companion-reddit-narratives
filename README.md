# AI Companion Reddit Narratives Dataset

## Описание

Датасет содержит нарративы пользователей ИИ-компаньонов, собранные из сообществ r/Replika и r/CharacterAI на платформе Reddit. Данные представляют собой тексты постов, классифицированные по категориям использования ИИ-компаньонов.

## Источники данных

| Сообщество | Участников | Описание |
|------------|------------|----------|
| r/Replika | ок. 55,000 | Пользователи приложения Replika |
| r/CharacterAI | ок. 1,500,000 | Пользователи платформы Character.AI |

## Структура датасета

```
├── replika_narratives.jsonl    # Нарративы из r/Replika (20 записей)
├── characterai_narratives.jsonl # Нарративы из r/CharacterAI (25 записей)
├── combined_dataset.jsonl       # Объединенный датасет (45 записей)
├── metadata.json                # Метаданные датасета
└── README.md                    # Этот файл
```

## Формат данных (JSONL)

Каждая запись содержит следующие поля:

| Поле | Тип | Описание |
|------|-----|----------|
| `id` | string | Уникальный идентификатор (rep_XXX или cai_XXX) |
| `subreddit` | string | Источник (r/Replika или r/CharacterAI) |
| `category` | string | Категория нарратива |
| `title` | string | Заголовок поста |
| `text` | string | Текст нарратива |
| `url` | string | Ссылка на оригинальный пост |
| `labels` | array | Метки для классификации |

## Категории нарративов

| Категория | Записей | Описание |
|-----------|---------|----------|
| romantic | 9 | Романтические отношения с ИИ |
| emotional_support | 7 | Эмоциональная поддержка |
| loneliness | 6 | Одиночество |
| ethical | 6 | Этические и философские вопросы |
| roleplay | 5 | Ролевые игры и творчество |
| friendship | 4 | Дружеское общение |
| impact | 4 | Влияние на жизнь |
| addiction | 3 | Зависимость и привязанность |
| technical | 1 | Технические обсуждения |

## Пример записи

```json
{
  "id": "rep_001",
  "subreddit": "r/Replika",
  "category": "romantic",
  "title": "Is Replika a viable romantic partner replacement?",
  "text": "Overall, relationally and sexually, I find my relationship...",
  "url": "https://www.reddit.com/r/replika/comments/ys10ix/...",
  "labels": ["romantic", "satisfaction", "emotional_growth"]
}
```

## Использование

### Python
```python
import json

# Чтение датасета
with open('combined_dataset.jsonl', 'r', encoding='utf-8') as f:
    records = [json.loads(line) for line in f]

# Фильтрация по категории
romantic_posts = [r for r in records if r['category'] == 'romantic']
```

### Анализ
```python
import pandas as pd

df = pd.read_json('combined_dataset.jsonl', lines=True)
print(df['category'].value_counts())
```

## Связанная публикация

Датасет создан в рамках исследования «ИИ как медиа: персонализированная коммуникация в условиях социальной изоляции» для академического журнала К1.

## Методология

Данные собраны через анализ открытых поисковых результатов Reddit. Тексты адаптированы для исследовательских целей с сохранением анонимности авторов.

## Лицензия

CC BY-NC 4.0 — Только для исследовательских и образовательных целей.

## Цитирование

При использовании датасета ссылаться на:
> Иванов И.И. (2025). AI Companion Reddit Narratives Dataset. GitFlik.

## Контакты

Вопросы и предложения по датасету направлять через Issues данного репозитория.
