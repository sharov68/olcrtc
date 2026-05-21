Как влить origin/master в форк
Стандартная последовательность:

# 1. Скачать свежий upstream (openlibrecommunity), не трогая ваш fork
git fetch origin
# 2. На своей ветке (у вас master) влить изменения
git merge origin/master
# или, если предпочитаете линейную историю:
# git rebase origin/master
# 3. Если были конфликты — исправить, затем:
git add .
git commit   # только если merge не завершился сам
# 4. Отправить обновлённый master в форк
git push fork master
# или просто git push — если upstream уже fork/master
origin здесь — только чтение upstream. В openlibrecommunity вы ничего не пушите.

## Деплой сервера/клиента с форка

`script/srv.sh` и `script/cnc.sh` по умолчанию клонируют **upstream**. Чтобы собрать код с фиксами из форка:

```bash
export OLCRTC_REPO_URL=https://github.com/sharov68/olcrtc.git
./script/srv.sh
```

Если на сервере уже есть `git pull` в `~/olcrtc`:

```bash
export OLCRTC_SOURCE_DIR=$HOME/olcrtc
./script/srv.sh
```
