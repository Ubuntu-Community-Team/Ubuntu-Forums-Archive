---
title: "Hide the contents of the Windows"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by smemamian on 2012-06-23
hi
How can I hide content that is in Windows?

For example, there are images in this folder:[/COLOR][/B]

[http://www.4myup.com/images/74608517768091096913.png](http://www.4myup.com/images/74608517768091096913.png)

---

### Post by ajgreeny on 2012-06-23
Use **nautilus ->Edit ->Preferences ->Preview** tab and set it to not show previews.  You will then just see the normal icon for file-type or folder.

---

### Post by smemamian on 2012-06-23
It had no effect:(

Album art is still shown :(


[/B][/COLOR]

---

### Post by HiImTye on 2012-06-23
delete your thumbnail cache and see if that fixes it
```
rm -Rf $HOME/.thumbnails
```

---

### Post by ajgreeny on 2012-06-23
> **HiImTye said:**
> delete your thumbnail cache and see if that fixes it
```
rm -Rf $HOME/.thumbnails
```
Be very careful with the **rm** command; there is no space after the $HOME/ part of the ccommand, though it looks as if there is.  One slip or typo and you could delete all your home folders and files.

It is worth having an alias of** rm -i** in place of **rm** to give you one more chance to stop the removal happening. Add the line ```
alias rm='rm -i'
```to your hidden **/home/user/.bash_aliases** file.

---

### Post by blackbird34 on 2012-06-23
[Bleachbit]("https://apps.ubuntu.com/cat/applications/bleachbit/") ( a little like CCleaner) can also delete your thumbnail cache more safely :-P

---

