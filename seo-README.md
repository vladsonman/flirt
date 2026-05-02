# DatingSearch SEO UA — Інструкція з розгортання

## Структура файлів

```
/
├── index.html      ← Головна сторінка (не чіпай)
├── config.json     ← ВСІ налаштування тут ★
├── manifest.json   ← PWA (можна не чіпати)
└── _redirects      ← Cloudflare Pages роутинг (не чіпай)
```

---

## Як розгорнути на Cloudflare Pages

1. Зайди на **pages.cloudflare.com**
2. Create a project → **Upload assets**
3. Завантаж всі 4 файли
4. Готово — отримай URL вигляду `твійсайт.pages.dev`

---

## Як керувати сайтом (тільки config.json)

### Підключити Google Таблицю
```json
"sheets": {
  "id": "ВСТАВЬ_ID_ТАБЛИЦЫ",
  "sheet_name": "Sheet1"
}
```
Замінити `ВСТАВЬ_ID_ТАБЛИЦЫ` на ID своєї таблиці.

---

### Змінити меню
```json
"nav": [
  { "label": "Топ сайтів",  "url": "/",         "active": true  },
  { "label": "Для дорослих","url": "/adult/",   "active": false },
  { "label": "Безкоштовні", "url": "/free/",    "active": false }
]
```
Щоб підкреслити активний пункт — `"active": true`.

---

### Змінити хлібні крихти
```json
"breadcrumbs": [
  { "label": "Головна",   "url": "/" },
  { "label": "Категорія", "url": "/category/" },
  { "label": "Поточна сторінка", "url": null }
]
```
Остання крихта завжди `"url": null` (поточна сторінка).

---

### Змінити FAQ
```json
"faq": [
  {
    "q": "Ваше питання?",
    "a": "Ваша відповідь."
  }
]
```
Google може показувати FAQ прямо в пошуковій видачі (rich snippet).

---

### Змінити блок "Як ми оцінюємо"
```json
"how_we_rate": {
  "title": "Як ми оцінюємо сайти",
  "criteria": [
    { "name": "Реєстрація", "desc": "Швидкість та зручність" }
  ]
}
```

---

### Змінити плашки довіри
```json
"trust_bar": [
  { "icon": "✓", "text": "Незалежні огляди" },
  { "icon": "🔒", "text": "Перевірені сайти" }
]
```

---

### SEO налаштування
```json
"page": {
  "h1": "Заголовок сторінки",
  "intro": "Вступний текст під заголовком (важливо для SEO)",
  "meta_title": "Тег title для Google",
  "meta_desc": "Тег description для Google (до 160 символів)"
}
```

---

## Структура Google Таблиці

Перший рядок — заголовки:

| geo | id | name | domain | tagline | logo | badge | rating | users | url | color | order | pinned | perks |
|-----|----|----|--------|---------|------|-------|--------|-------|-----|-------|-------|--------|-------|
| ua | ua_1 | FlirtUA | flirt.ua | Знайди пару | 💛 | ТОП | 4.9 | 800K | https://... | #f59e0b | 1 | FALSE | Безкоштовно, Реальні анкети |

**Нові колонки порівняно з попередніми версіями:**
- `domain` — домен для зеленого рядка під назвою (якщо порожньо — береться з URL)

---

## SEO що вже вбудовано

- ✅ Schema.org ItemList (список офферів)
- ✅ Schema.org FAQPage (блок питань)
- ✅ Schema.org BreadcrumbList (хлібні крихти)
- ✅ Open Graph теги
- ✅ hreflang (uk/en)
- ✅ Canonical URL
- ✅ meta title та description
- ✅ Семантичний HTML (article, nav, main, h1, h2)
- ✅ Дисклеймер про партнерські посилання
- ✅ rel="noopener sponsored" на посиланнях

---

## Що додати пізніше

- [ ] robots.txt
- [ ] sitemap.xml
- [ ] Іконки PWA (icons/icon-192.png, icons/icon-512.png)
- [ ] Google Analytics / Tag Manager
- [ ] Сторінки під кожну категорію (/serious/, /adult/, /ai/)
