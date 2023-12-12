## Домашнее задание к занятию «Репликация и масштабирование. Часть 1»
Инструкция по выполнению домашнего задания
1. Сделайте fork репозитория c шаблоном решения к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды git clone.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
 - впишите вверху название занятия и ваши фамилию и имя;
 - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
 - для корректного добавления скриншотов воспользуйтесь инструкцией «Как вставить скриншот в шаблон с решением»;
 - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в инструкции по MarkDown.
4. После завершения работы над домашним заданием сделайте коммит (git commit -m "comment") и отправьте его на Github (git push origin).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.
_______________

### Задание 1
На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.

Ответить в свободной форме.

     ##### Репликация Master-Slave
В этом подходе существует один основной сервер, который называется Мастером – на нем происходят все изменения данных. Слейв-сервер должен копировать все изменения, происходящие на Мастере. Для чтения данных приложение отправляет запросы на Слейв, а Мастер отвечает только за запись и изменения. В этой системе может быть несколько Слейв-серверов.

     ##### Репликация Master-Master
Master-Master репликация В этой схеме любой сервер может быть использован для изменения и чтения данных, при этом происходящие на нем изменения будут продублированы на другой сервер. Мастер-мастер в режиме active-active: этот вариант известен как двунаправленная репликация. Каждый из двух серверов выступает одновременно в качестве мастера и в качестве слэйва. В этом варианте есть проблема с разрешением конфликтов, когда, например, два запроса начинают одновременно менять одну и ту же строку или когда происходит одновременная автоинкрементная вставка в таблицу на оба сервера.

Основное отличие между режимами заключается в том, что в режиме master-slave, slave могут только принимать запросы на чтение, в то время как master может производить операции записи и операции чтения. В master-master каждый master может производить операции записи и чтения. Master-master имеет больше пропускной способности, но также как и master-slave не поддерживает транзакции, сравнимо медленнее master-slave и менее отказоустойчив.

### Задание 2
Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.

Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.

   ![image](https://github.com/vioas/Replication-and-scaling.-1-/assets/142601752/714cd4c7-5e19-42f8-898c-fa94571aa343)


### Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
Выполните конфигурацию master-master репликации. Произведите проверку.

Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.
