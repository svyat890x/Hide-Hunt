# Hide Hunt: Android-версія (Capacitor)

## 1. Що встановити (один раз)
- Node.js (nodejs.org, версія LTS)
- Android Studio (developer.android.com/studio)

## 2. Firebase (щоб гравці бачили одне одного на різних телефонах)
1. Зайди на console.firebase.google.com, створи проєкт (безкоштовно).
2. Додай веб-застосунок (іконка </>) і скопіюй об'єкт firebaseConfig.
3. Відкрий www/index.html, знайди FIREBASE_CONFIG і встав свої значення замість PASTE_HERE та порожніх полів.
4. У Firebase: Build > Firestore Database > Create database > Start in test mode.
   Test mode діє ~30 днів. Потім потрібні правила доступу.
Без цього гра працює лише на одному телефоні (демо-режим).

## 3. Збірка
У папці проєкту виконай:
```
npm install
npx cap add android
```

## 4. Дозволи на GPS
Відкрий android/app/src/main/AndroidManifest.xml і додай перед `<application`:
```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

## 5. Запуск на телефоні
```
npx cap sync
npx cap open android
```
В Android Studio підключи телефон (режим розробника + USB-налагодження) і натисни Run.
Щоб отримати файл .apk: Build > Build Bundle(s) / APK(s) > Build APK(s).

Після кожної зміни в www/index.html виконуй `npx cap sync`.

---
## Спосіб без Android Studio: APK збирає GitHub
1. Створи безкоштовний акаунт на github.com і новий репозиторій.
2. Завантаж у нього весь вміст цієї папки (Add file > Upload files), разом із прихованою папкою .github.
3. Відкрий вкладку Actions > Build APK > Run workflow.
4. Через 5-10 хвилин у запуску з'явиться файл hide-hunt-apk. Завантаж, розпакуй, перекинь app-debug.apk на телефон і встанови (дозволь установку з невідомих джерел).
