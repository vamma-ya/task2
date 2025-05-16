# task2


    import requests
    from bs4 import BeautifulSoup
    import csv

    alphabet = 'АБВГДЕЁЖЗИЙКЛМНОПРСТУФХЦЧШЩЫЭЮЯ'
    base_url = 'https://ru.wikipedia.org/wiki/Категория:Животные_по_алфавиту_'

    with open('beasts.csv', 'w', newline='', encoding='utf-8') as f:
        writer = csv.writer(f)
        for letter in alphabet:
            url = base_url + letter
            r = requests.get(url)
            soup = BeautifulSoup(r.text, 'html.parser')
            count = len(soup.select('.mw-category-group a'))
            writer.writerow([letter, count])
            print(f"{letter}: {count}")
