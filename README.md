Ansible роль ПК ТА
=========

Роль для установки и настройки ПК ТА.

- Создает директории для изменяемых и неизменяемых данных.
- Копирует все файлы Docker в директорию с неизменяемыми данными.
- Настаивает конфигурационные файлы для запуска контейнеров.
- Регистрирует сервисы в домене и запрашивает их keytab-файлы.

Требования
------------

Роль предназначена для использования в операционных системах:

- Astra Linux 1.7

Параметры роли
--------------

| Название                   | Значение по умолчанию                  |  Описание                               |
|----------------------------|----------------------------------------|-----------------------------------------|
| niitp_tasp_user            | tasp                                   | Пользователь для запуска ПК ТА          |
| niitp_tasp_group           | opertasp                               | Группа для запуска ПК ТА                |
| niitp_tasp_maclabel        | 0                                      | Мандатная метка запущенных контейнеров  |
| niitp_tasp_dir             | /spo/niitp/tasp                        | Директория установки ПК ТА              |
| niitp_tasp_auth_gss        | false                                  | Флаг включения аутентификации GSS       |
| niitp_tasp_docker_volume   | /var/spo/niitp/tasp                    | Директория изменяемых файлов ПК ТА      |
| niitp_tasp_pg_port         | 5433                                   | Порт СУБД                               |
| niitp_tasp_proxy_port      | 8080                                   | Порт реверсивного прокси                |
| niitp_tasp_proxy_keytab    | /var/spo/niitp/tasp/proxy/proxy.keytab | Путь к keytab файлу реверсивного прокси |
| niitp_tasp_proxy_log_level | info                                   | Уровень логирования реверсивного прокси |
| niitp_tasp_proxy_principle | HTTP/tasp.t500.ar                      | Название сервиса прокси во FreeIPA      |
| niitp_tasp_ui_log_level    | info                                   | Уровень логирования интерфейса          |
| niitp_tasp_ipa_host        | dc.t500.ar                             | Адрес FreeIPA                           |
| niitp_tasp_ipa_user        | admin                                  | Пользователь FreeIPA                    |
| niitp_tasp_ipa_pass        | 12345678                               | Пароль пользователя FreeIPA             |

Зависимости
------------

Зависимости отсутствуют

Пример использования
----------------

В репозитории содержатся параметры для установки и настройки ПК ТА
в директории [environments/tasp](./environments/tasp)

    - hosts: all
      roles:
         - niitp.tasp

```sh
ansible-playbook site.yml
```
