---
title: "how to get date package was installed?"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-02-02
IN Snyaptic package manager if I rightclick on a package in the list it gives me all kinds of info but not the date when it was installed - how do I get that?

---

### Post by lechien73 on 2012-02-02
I believe that the system currently doesn't store or display the date that a package was installed.

You can find the information in the /var/log/dpkg.log file. These files rotate and the backups get stored in .gz archives, so you might have to extract them if you're looking for specific packages.

Just by way of example, open a terminal window and try:

```
cat /var/log/dpkg.log | grep "\ install\ "
```

You can also do this with dpkg.log.1 and the files you extract from the .gz archives.

---

### Post by nothingspecial on 2012-02-02
/var/log/apt/history.log will show you the date.

---

### Post by satanselbow on 2012-02-02
Update Manager also has a View -> History of Updates

Anything installed from a tarball would provide the "last changed date" as an indication as "create date" is not recorded.

```
stat <executable-path>
```

---

### Post by chickenPie4breakfast on 2012-02-02
Thanks for the help - one more question
is there some sort of command or commands that could remove all packages installed today - that is on a particular day? this would be a lot easier than having to specify them all - one by one

---

### Post by Dennis N on 2012-02-02
> **satanselbow said:**
> Update Manager also has a View -> History of Updates...


I was looking for this View menu item, and it appears Update Manager displays no menu at all if you have the global menu disabled? This is unusual. All other applications I have checked display a traditional menu bar within the application window.

---

### Post by lechien73 on 2012-02-02
> **chickenPie4breakfast said:**
> Thanks for the help - one more question
is there some sort of command or commands that could remove all packages installed today - that is on a particular day? this would be a lot easier than having to specify them all - one by one

Yes, you can...the following code will do this:

```
cat /var/log/apt/history.log | grep -A1 "`date +%Y-%m-%d`" | grep "\ install\ " | awk -F" " '{printf $4 " "}'  | xargs sudo apt-get remove -y
```

What it does is this:

1. Processes the contents of the apt history.log file by selecting only the packages installed today.

2. awk outputs the package name only, strips the newline character.

3. This is piped into apt-get using xargs

4. apt-get has the -y switch set to auto answer yes to all questions. Remove the -y switch if you want a bit more control over what's going on.

If you want to see what packages would be removed, then try the following command:

```
cat /var/log/apt/history.log | grep -A1 "`date +%Y-%m-%d`" | grep "\ install\ " | awk -F" " '{print $4 " "}'
```

This will give you a package list. Also note that it only works for today's date.

I've tested this and it protects Ubuntu upgrades, and only targets packages that were actually installed using apt-get.

---

### Post by chickenPie4breakfast on 2012-02-02
Thanks [U]lechien73
that will come in handy
[/U]

---

