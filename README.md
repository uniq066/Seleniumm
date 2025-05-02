# Seleniumm

1. **Автоматизация поиска в Google**.
2. **Скриншот страницы**.
3. **автоматизации тестирования**. 

 1. Автоматизация поиска в Google

Этот скрипт открывает Google, вводит поисковый запрос и выводит заголовки первых 5 результатов.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Настройка драйвера
driver = webdriver.Chrome()
driver.get("https://google.com")

# Поиск по запросу
search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Selenium Python" + Keys.RETURN)

# Ожидание загрузки результатов
time.sleep(2)

# Получение заголовков первых 5 результатов
results = driver.find_elements(By.CSS_SELECTOR, 'h3')[:5]
for index, result in enumerate(results):
    print(f"{index + 1}: {result.text}")

# Закрытие браузера
driver.quit()
```

 2. Скриншот страницы

Этот скрипт открывает сайт и делает его скриншот.

```python
from selenium import webdriver

# Настройка драйвера
driver = webdriver.Chrome()
driver.get("https://4pda.to")  

# Сохранение скриншота
driver.save_screenshot("screenshot.png")

# Закрытие браузера
driver.quit()
```



3. Автоматизация тестирования веб-страницы

В этом примере мы будем проверять, что заголовок страницы соответствует ожидаемому значению.

```python
import unittest
from selenium import webdriver
from selenium.webdriver.common.by import By

class TestWebPageTitle(unittest.TestCase):

    @classmethod
    def setUpClass(cls):
        # Настройка драйвера перед запуском тестов
        cls.driver = webdriver.Chrome()
        cls.driver.get("https://4pda.to")  

    def test_title(self):
        # Проверка заголовка страницы
        expected_title = "4pda"  
        actual_title = self.driver.title
        self.assertEqual(actual_title, expected_title, f"Заголовок страницы '{actual_title}' не соответствует ожидаемому '{expected_title}'")

    @classmethod
    def tearDownClass(cls):
        # Закрытие драйвера после завершения тестов
        cls.driver.quit()

if __name__ == "__main__":
    unittest.main()
```

