---
title: "PHP invisible for 'sudo'"
date: 2014-04-29
forum: Programming Talk
---

### Post by alan24 on 2014-04-29
Hi,

I need to use PHP in sudo mode(for creating new Yii project).

When I type:
```
sudo yii-project/framework/yiic webapp yiidemo
```  from my htdocs dicectory(XAMPP) the message I get is:

  ```
/usr/bin/env: php: No such file or directory
```When I type 'php -v' I get standard version info. When I type 'sudo php -v' I get a message 'sudo: php: Command not found'.

'echo $PATH' and 'sudo echo $PATH' produce identical strings. I have PHP installed under XAMPP folder in /opt/lampp/bin.
```

echo $PATH
/home/alan/home/alan/netbeans-8.0/bin/netbeans/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/lampp/bin

sudo echo $PATH
/home/alan/home/alan/netbeans-8.0/bin/netbeans/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/lampp/bin
```

Would you have any suggestions? Thanks:)!

---

### Post by spjackson on 2014-04-29
[QUOTE]
```

sudo echo $PATH

```
[QUOTE]
doesn't do what you think it does. (PATH is translated by your current shell then the result is passed to sudo echo.)
```

sudo /usr/bin/printenv PATH

```
should give you an idea what's going on.

---

### Post by SeijiSensei on 2014-04-29
When you run a command with sudo, I'm pretty sure it uses root's environment, not yours.

Why not just install PHP from the repositories where it will appear as /usr/bin/php and be available to everyone?  If you just need the command-line parser, install the **php5-cli** package.

---

### Post by alan24 on 2014-04-29
@spjackson: thanks, it worked. It seems that there is no php directory in sudo PATH.

@SeijiSensei: thanks! I've installed **php5-cli** and sudo php -v works. I can create a yii application as well.

---

