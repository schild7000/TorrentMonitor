# TorrentMonitor
Приложение мониторит изменения на популярных торрент-трекерах рунета и автоматизирует закачку обновлений (сериалы, раздачи которые ведутся *путем добавления новых серий/новых версий*, перезалитые торрент-файлы и т.д.)

###Список возможностей приложения:

* Слежение за темами на nnm-club.ru
* Слежение за темами на rutracker.org
* Слежение за темами на rutor.org
* Слежение за релизерами на nnm-club.ru
* Слежение за релизерами на rutracker.org
* Поиск новых серий на lostfilm.tv
* Поиск новых серий на novafilm.tv

###Скриншоты:
![Screenshot1](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый11.png "Screenshot1")
![Screenshot2](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый.png "Screenshot2")
![Screenshot3](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый21.png "Screenshot3")
![Screenshot4](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый3.png "Screenshot4")
![Screenshot5](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый4.png "Screenshot5")
![Screenshot6](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый5.png "Screenshot6")
![Screenshot7](http://blog.korphome.ru/wp-content/uploads/2011/02/Новый6.png "Screenshot7")


###Требования для установки:

* Веб-сервер (Apache, nginx, lighttpd)
* PHP (5.2 или выше) с поддержкой cURL и PDO
* MySQL

###Установка:

* Импортировать дамп базы из директории db_schema в зависимости от используемой БД - *.sql
* Перенести все файлы в папку на вашем сервере (например /path/to/folder/torrent_monitor/)
* Внести изменения в config.php и указать данные для доступа к БД
* Добавить в cron engine.php ( *проверьте права на запись в каталог /path/to/log/* )

```
*/10 * * * * php -q /path/to/folder/torrent_monitor/engine.php >> /path/to/log/torrent_monitor_error.log 2>&1
```
* Зайти в веб-интерфейс ( **пароль по умолчанию — torrentmonitor, смените(!) его после первого входа** )
* Указать учётные данные от трекеров
* Указать в настройках путь для сохранения торрентов (папка, которая мониторится вашим торрент-клиентом), e-mail и разрешить/запретить отправку 
уведомлений
* Добавить торренты для мониторинга
* Перейти на вкладку «Тест» и проверить — всё ли верно работает


###Настройки:

Так же, в php.ini (для CLI) необходимо изменить следующие параметры:

```
; увеличить максимальное вермя выполнения скрипта
max_execution_time = 300

; указать date.timezone
date.timezone = Europe/Moscow

; эту опцию желательно включить в php.ini как для CLI, так и для веб-сервера
allow_url_fopen = on

; проверить - разрешена ли запись в сторонние каталоги. 
; Нужно разрешить запись в каталог с самим приложением TorrentMonitor 
; и каталог куда будут сохраняться *.torrent файлы для torrent клиента
open_basedir = /tmp/:/path/to/folder/torrent_monitor/:/path/to/folder/torrent_client_watch/
```

###Обновление:

Наилучшим, и самым простым, способом обновления приложения является удаление всех файлов, кроме config.php и заливкой новой версии. Также, если в обновлении имеется update.sql, его необходимо выполнить в вашей базе данных.

###Страница проекта:

[blog.korphome.ru](http://blog.korphome.ru/torrentmonitor/)