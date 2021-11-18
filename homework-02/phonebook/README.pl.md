**Читать на других языках: Czytaj w innych językach [rosyjski](README.md), [ukraiński](README.ua.md).**

# Телефонная книга Książka telefoniczna

Напиши приложение хранения контактов телефонной книги.
Napisz aplikację do przechowywania kontaktów z książki telefonicznej.

## Шаг 1 Krok 1

Приложение должно состоять из формы и списка контактов. На текущем шаге реализуй
добавление имени контакта и отображение списка контактов. Приложение не должно
сохранять контакты между разными сессиями (обновление страницы).

Aplikacja powinna składać się z formularza i listy kontaktów. W tym kroku zrealizuj dodanie nazwy kontaktu i wyświetlanie listy kontaktów. Aplikacja nie powinna zapisywać kontaktów między różnymi sesjami (aktualizacja stony).

Используй эту разметку инпута с встроенной валидацией для имени контакта.
Wykorzystaj ten ukłąd input z wmontowaną walidacją nazwy kontaktu.


```html
<input
  type="text"
  name="name"
  pattern="^[a-zA-Zа-яА-Я]+(([' -][a-zA-Zа-яА-Я ])?[a-zA-Zа-яА-Я]*)*$"
  title="Name may contain only letters, apostrophe, dash and spaces. For example Adrian, Jacob Mercer, Charles de Batz de Castelmore d'Artagnan"
  required
/>
```

Состояние хранящееся в родительском компоненте `<App>` обязательно должно быть
следующего вида, добавлять новые свойства нельзя.

Stan przechowywany w komponencie rodzicu `<App>` powinno wyglądać następująco, nie należy dodawać nowych własciwości.

```bash
state = {
  contacts: [],
  name: ''
}
```

Каждый контакт должен быть объектом со свойствами `name` и `id`. Для генерации
идентификаторов используй любой подходящий пакет, например
[nanoid](https://www.npmjs.com/package/nanoid). После завершения этого шага,
приложение должно выглядеть примерно так.

Każdy kontakt powinien być obiektem z właściwościami `name` i `id`. Do generowania identyfikatoró∑ wykorzystaj dowolną pasującą paczkę, na przykład [nanoid](https://www.npmjs.com/package/nanoid). Po tym kroku aplikcja powinna wyglądać mniej więcej tak.

![preview](./mockup/step-1.png)

## Шаг 2 Krok 2

Расширь функционал приложения, позволив пользователям добавлять номера
телефонов. Для этого добавь `<input type="tel">` в форму, и свойство для
хранения его значения в состоянии.

Rozszerz funkcjonalność aplikacji, pozwalając użytkownikom dodawać numery telefonów. W tym celu dodaj do formularza `<input type="tel">` oraz właściwość dla przechowywania jego wartości w stanie.

```bash
state = {
  contacts: [],
  name: '',
  number: ''
}
```

Используй эту разметку инпута с встроенной валидацией для номера контакта.
Wykorzystaj układ input z wmontowaną walidacją numeru kontaktu.

```html
<input
  type="tel"
  name="number"
  pattern="\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}"
  title="Phone number must be digits and can contain spaces, dashes, parentheses and can start with +"
  required
/>
```

После завершения этого шага, приложение должно выглядеть примерно так.
Po tym kroku aplikacja powinn działać mniej więcej tak.

![preview](./mockup/step-2.png)

## Шаг 3 Krok 3

Добавь поле поиска, которое можно использовать для фильтрации списка контактов
по имени.

Dodaj pole wyszukiwania, które można wykorzystać do filtrowania listy kontaktów po nazwie.

- Поле поиска это инпут без формы, значение которого записывается в состояние
  (контролируемый элемент).
  Pole wyszukiwania to input bez formularza, którego wartość zapisuje się w stanie (kontrolowany element).
- Логика фильтрации должна быть нечувствительна к регистру.
- Logika filtrowania powinna być niewrażliwa na wielkość liter.

```bash
state = {
  contacts: [],
  filter: '',
  name: '',
  number: ''
}
```

![preview](./mockup/step-3.gif)

Когда мы работаем над новым функционалом, бывает удобно жестко закодировать
некоторые данные в состояние. Это избавит от необходимости вручную вводить
данные в интерфейсе для тестирования работы нового функционала. Например можно
использовать такое начальное состояние.

Gdy pracujemy nad nową funkcjonalnością, może być wygodne twarde zakodowanie niektórych danych w stanie. Sprawi to, że nie będziemy musieli ręcznie wprowadzać danych do interfejsu, aby przetestować pracę nowej funkcjonlności. Można na przykład wykorzystać taki stan początkowy.

```bash
state = {
  contacts: [
    {id: 'id-1', name: 'Rosie Simpson', number: '459-12-56'},
    {id: 'id-2', name: 'Hermione Kline', number: '443-89-12'},
    {id: 'id-3', name: 'Eden Clements', number: '645-17-79'},
    {id: 'id-4', name: 'Annie Copeland', number: '227-91-26'},
  ],
  filter: '',
  name: '',
  number: ''
}
```

## Шаг 4 Krok 4

Если твое приложение реализовано в одном компоненте `<App>`, выполни
рефакторинг, выделив подходящие части в отдельные компоненты. В состоянии
корневого компонента `<App>` останутся только свойства `contacts` и `filter`.

Jeżeli twoja aplikcja jest realizowana w jednym komponencie `<App>`, wykonaj refaktor, rozdzielając pasujące części do oddzielnych komponentów. W stanie głównego komponentu `<App>` zostaną tylko właściwości `contacts` i `filter`.

```bash
state = {
  contacts: [],
  filter: ''
}
```

Достаточно выделить четыре компонента: форма добавления контактов, список
контактов, элемент списка контактов и фильтр поиска.

Wystarczy wydzielić cztery komponenty: formularz dodania kontaktów, listę kontaktów, element listy kontaktów i filtr wyszukiwania.

После рефакторинга корневой компонент приложения будет выглядеть так.
Po refaktorze źródłowy komponent aplikacja będzie wyglądał tak.

```jsx
<div>
  <h1>Phonebook</h1>
  <ContactForm ... />

  <h2>Contacts</h2>
  <Filter ... />
  <ContactList ... />
</div>
```

## Шаг 5 Krok 5

Запрети пользователю возможность добавлять контакты, имена которых уже есть в
телефонной книге. При попытке выполнить такое действие выведи `alert` с
предупреждением.

Wyłącz użytkownikowi możliwość dodawania kontaktów, których nazwy są już w książce telefonicznej. W razie próby wykonania takiego działania, pokaż `alert` z ostrzeżeniem.

![preview](./mockup/step-5.png)

## Шаг 6 Krok 6

Расширь функционал приложения, позволив пользователю удалять ранее сохраненные
контакты.

Rozszerz funkcjonalność aplikacji, pozwalając użytkownikowi usuwać wcześniej zapisane kontakty.

![preview](./mockup/step-6.gif)