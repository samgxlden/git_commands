# git_commands

## https://githowto.com/ru

## Полезные команды

```ls``` - проверить что лежит в папке.

```cd путь``` - переход по нужному пути.

```mkdir имя папки``` - создает папку.

```touch имя файла``` - создает файл.

```git log --pretty=oneline``` - однострочный просмотр изменений.

```cat файл``` - просмотреть содержимое файла.

```git rm -r имя директории``` - удаление директории, при непроиндексированном изменении гит будет ругаться.

```git rm -f имя файла``` - удаляет непроиндексированный файл.

```git mv index.html hello.html``` - переименует файл index.html в hello.html.

## Коммиты

```git commit -am "commit"``` - закоммитить все измененные файлы одним коммитом. С этой командой нужно быть осторожнее, чтобы не закоммитить лишнего.

```git commit -m "commit" файл``` - создать коммит нужного файла.

## Снять индексацию с проиндексированного файла

```git reset файл``` - снять индексацию с add файла.

```git reset HEAD файл``` - снять индексацию с add файла, но не измененяет рабочий каталог. Чтобы удалить нежелательные изменения нужно сделать ```git checkout файл```.

## Алиасы

```git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"``` - алиас для просмотра истории.

```git config --global alias.go checkout``` - алиас checkout.

## Теги

```git tag имя тега``` - создать тег.

```git tag``` - просмотреть доступные теги.

```git hist master --all``` - просмотреть теги в коммитах.

```git tag v1``` - создание тега версии.

```git tag v1^``` - переход к предыдущей версии.

## Откат последнего изменения в файле

```git checkout файл``` - откат последнего изменения в файле.

```git revert HEAD --no-edit``` - откат на предыдущий коммит без открытия в редакторе.

```git reset --hard к чему откат (хеш коммита, тег)``` - откат к нужному коммиту либо тегу.

```git tag -d tag name``` - удаление тега (вместе с ним потруться все коммиты, которые в нем были). 

```git commit --amend -m "commit"``` - изменение предыдущего коммита (если забыл что-то добавить), чтобы обойтись одним коммитом.

## Спрятать изменения

```git stash``` - спрятать изменения.

```git stash apply``` - показать спрятаные изменения.

## Ветки

```git branch``` - посмотреть доступные ветки.

```git branch -a``` - посмотреть все ветки, включая удаленные.

```git branch имя ветки``` - создает ветку.

```git checkout -b имя ветки``` - создать ветку и переключится на нее.

```git checkout имя ветки``` - переключиться на нужную ветку.

## Слияние 

```git merge ветка``` - слить включенную ветку с которой мы хотим, если возникли конфликты необходимо их решить. После решения конфликтов проиндексировать файлы и сделать их коммит.

```git merge --no-ff ветка``` - флаг --no-ff вынуждает Git всегда создавать новый объект коммита при слиянии. Это позволяет не терять информацию о том, что ветка существовала, и группирует вместе все внесённые изменения. Таким образом можно отследить какая группа коммитов образует ту или иную функциональность.

## Сброс ветки

```git reset --hard хеш коммита``` - сбросить ветку к нужному коммиту.

## Перебазирование

```git rebase имя ветки``` - перебазирует изменения из нужной ветки во включенную. Конечный результат перебазирования очень похож на результат слияния. Однако из нужной ветки прилетят все коммиты.

Не используйте перебазировние:

* Если ветка является публичной и расшаренной. Переписывание общих веток будет мешать работе других членов команды.

* Когда важна точная история коммитов ветки (так как команда rebase переписывает историю коммитов).

## Удаленные репозитории

```git clone имя репозитория имя клона``` - сначала нужно от корня репозитория выполнить команду ```cd ..``` , далее выполнить команду клонирования.

```git remote``` - узнать об именах удаленных репозиториев.

```git fetch``` - извлекает новые коммиты из удаленного репозитория, но не сливает их с наработками в локальном репозитории.

```git merge origin/master``` - сливает удаленный репозиторий с локальным после извлеченных изменений.

```git pull origin master``` - выполняет сразу две команды ```git fetch``` и ```git merge origin/master```.

```git branch --track style origin/style``` - добавить локальную ветку style, которая отслеживает удаленную ветку origin/style.

## Чистые репозитории

```git clone --bare hello hello.git``` - создает чистый репозиторий директории hello.

```git remote add shared ../hello.git``` - добавление удаленного чистого репозитория к нашему оригинальному.

## Отправка изменений 

```git push origin master``` - отправка измений в ветку мастер.

https://githowto.com/ru/rebasing
