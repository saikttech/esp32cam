# 📹 ESP32-CAM Hi-Tech WiFi Camera

<div align="center">

![ESP32-CAM](https://img.shields.io/badge/ESP32-CAM-orange?style=for-the-badge&logo=espressif)
![Arduino IDE](https://img.shields.io/badge/Arduino-IDE-00878F?style=for-the-badge&logo=arduino)
![WiFi](https://img.shields.io/badge/WiFi-AP%20Mode-blue?style=for-the-badge&logo=wifi)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-1.0.0-purple?style=for-the-badge)

**Профессиональная система видеонаблюдения на базе ESP32-CAM с Hi-Tech веб-интерфейсом**

[Возможности](#-возможности) • [Установка](#-установка) • [Использование](#-использование) • [API](#-api-endpoints) • [FAQ](#-faq)

</div>

---

## 📖 Описание

**ESP32-CAM Hi-Tech Camera** — это полнофункциональная система видеонаблюдения на микроконтроллере ESP32-CAM (AI-Thinker) с современным киберпанк-интерфейсом. Устройство работает как автономная WiFi точка доступа с веб-интерфейсом для управления камерой, записи видео на SD-карту и детекции движения.

### 🎯 Ключевые особенности

- **Автономная работа** — создаёт собственную WiFi сеть, не требует роутера
- **Hi-Tech дизайн** — неоновый киберпанк интерфейс с cyan/magenta акцентами
- **MJPEG видеопоток** — реальное время с настраиваемым качеством (QVGA → UXGA)
- **Запись на SD-карту** — ручной режим или автоматическая запись при движении
- **Motion Detection** — программная детекция движения через сравнение кадров
- **Умное управление памятью** — автоматическое удаление старых файлов при заполнении (FIFO)
- **Безопасность** — HTTP Basic Auth защита (admin/admin)
- **Адаптивный дизайн** — работает на ПК, планшетах и смартфонах

---

## ✨ Возможности

### 🎥 Видеонаблюдение
- ✅ MJPEG видеопоток в реальном времени (~15-30 FPS)
- ✅ Сворачиваемый видеоплеер (экономия ресурсов при сворачивании)
- ✅ 9 уровней качества: от QVGA (320×240) до UXGA (1600×1200)
- ✅ Одиночный снимок с возможностью скачивания

### 💾 Запись на SD-карту
- ✅ **Ручной режим** — запись по нажатию кнопки REC
- ✅ **Режим детекции движения** — автоматическая запись при обнаружении движения
- ✅ Настраиваемая чувствительность motion detection
- ✅ Инкрементальные имена файлов (img_00001.jpg, img_00002.jpg, ...)

### 🗂️ Управление файлами
- ✅ Просмотр списка файлов с размерами
- ✅ Скачивание отдельных файлов
- ✅ Удаление файлов по одному
- ✅ Массовая очистка всех файлов
- ✅ **Автоматическое удаление** при заполнении SD-карты (FIFO)
- ✅ Настраиваемый порог автоудаления (70-99%)

### 🎨 Интерфейс
- ✅ Hi-Tech / Cyberpunk стиль
- ✅ Неоновые акценты (cyan #00ffff, magenta #ff00ff)
- ✅ Glow-эффекты и анимации
- ✅ Адаптивная вёрстка (CSS Grid/Flexbox)
- ✅ AJAX обновление статуса каждые 3 секунды
- ✅ Визуальный progress-bar заполнения SD-карты

### 🔒 Безопасность
- ✅ HTTP Basic Authentication
- ✅ Логин/пароль: `admin` / `admin`
- ✅ Защита всех endpoints

---

## 🔧 Требования

### Аппаратные требования

| Компонент | Минимум | Рекомендуется |
|-----------|---------|---------------|
| **Плата** | ESP32-CAM (AI-Thinker) | ESP32-CAM с антенной |
| **SD-карта** | MicroSD 4GB (FAT32) | MicroSD 16-32GB Class 10 |
| **Питание** | 5V 1A | 5V 2A блок питания |
| **USB-кабель** | Micro-USB (с передачей данных) | Качественный кабель |
| **Компьютер** | USB порт | USB 3.0 порт |

### Программные требования

- **Arduino IDE** 2.x или новее
- **ESP32 Board Package** 2.x или 3.x
- **Драйвер USB-UART** (CH340 / CP2102 / FTDI)
- **Веб-браузер** с поддержкой JavaScript (Chrome, Firefox, Edge, Safari)

---

## 🚀 Установка

### Шаг 1: Установка Arduino IDE

1. Скачайте Arduino IDE с [официального сайта](https://www.arduino.cc/en/software)
2. Установите и запустите

### Шаг 2: Добавление поддержки ESP32

1. Откройте **File → Preferences**
2. В поле **"Additional Board Manager URLs"** добавьте: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
3. Нажмите **OK**
4. Откройте **Tools → Board → Boards Manager**
5. Найдите **"esp32"** и установите последнюю версию
6. Перезапустите Arduino IDE

### Шаг 3: Установка драйверов

Определите чип USB-UART на вашей плате:

| Чип | Драйвер | Ссылка |
|-----|---------|--------|
| **CH340** | CH341SER | [Скачать](https://www.wch-ic.com/downloads/CH341SER_EXE.html) |
| **CP2102** | CP210x | [Скачать](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) |
| **FTDI** | CDM21228 | [Скачать](https://ftdichip.com/drivers/d2xx-drivers/) |

### Шаг 4: Загрузка прошивки

1. Скачайте или клонируйте репозиторий:
```bash
git clone https://github.com/yourusername/esp32-cam-hitech-camera.git

