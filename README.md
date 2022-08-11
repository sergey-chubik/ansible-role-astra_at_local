Ansible Role: Astra Atestat Local
=========

Эта роль выполнит настройку АРМ на базе ОС Astra Linux SE версий 1.5, 1.6, 1.7 в соответствии с требованиями безопасности для обработки конфеденциальной информации (аттестационные мероприятия). С помощью роли можно создать локальный репозиторий (main и update), установить оперативные обновления операционной системы, настроить загрузчик grub, создать пользователей в системе и настроить директории для хранения конфеденциальной информации с различным уровнем мандатного доступа. Предполагается что ISO-образы основного диска и диска с обновлениями расположены в домашней директории пользователя в директории astra, параметр `astra_at_local_iso_path: /home/user/astra`.

Requirements
------------

Для хоста, на котором запускается эта роль необходимы следующие требования:
```
sshpass
rsync
pexpect >= 3.3
```

Role Variables
--------------

Доступные переменные перечислены вместе со значениями по умолчанию в файле **defaults/main.yml**.
Переменные отвечающие за создание локального репозитория, репозитория диска с обновлениями, установку оперативных обновлений и обновление загрузчика grub (по умолчанию `false`):
```
astra_at_local_repo_main_create: false
astra_at_local_repo_update_create: false
astra_at_local_os_update: false
astra_at_local_grub_edit: false
```
Выбор способа установки обновления (штатный способ `dist_upgrade` или через утилиту `astra_update`, рекомендуемую разработчиками Astra):
```
astra_at_local_os_update_tool: astra_update
```
Переменная для создания локальных пользователей на ОС Astra Linux SE для работы под мандатным уровнем доступа (имя пользователей и общий пароль):
```
astra_at_local_users: 
  - user1
  - user2
astra_at_local_users_password: 1qaz!QAZ
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - astra_at_local

License
-------

BSD

Author Information
------------------

Chubik Sergey.
