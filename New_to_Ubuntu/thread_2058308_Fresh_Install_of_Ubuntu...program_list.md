---
title: "Fresh Install of Ubuntu...program list ?"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2012-09-15
I have been using Ubuntu on my main PC for nearly 2 years now, and have been here quite a few times for help. It took me a long time to get used to the big change from Windows (which i still have dual booting on another machine). :p

Over time i have installed (and un-installed) many programs to see which ones i like best.

I have decided its time to do a fresh instal rather than keep upgrading every time, and as Ubuntu 12.04.1 LTS is out i think its time.

I know over time i will remember all the programs i use at the moment (Thunderbird is now default, and i cannot survive without GIMP & VLC).

Is there anyway before i re-install that i can list all the programs installed on this PC just so i dont forget when i go back to the Software Centre which ones i need ?? 

Its not a major problem, but would just save time if i could get it done all in one go. There are some i dont want anymore and just wont bother to put back on.

Any help or advice would be great as usual ;)

---

### Post by hakermania on 2012-09-15
I guess the best thing you have to do is to right click on the Dash Home, select Applications and choose under 'Filter Results' "All". Under the Installed section you will find all of you applications.

If you want a cop-able list, I guess you can save the output of 
```

ls /usr/share/applications/

```
Note though that the above will not list the applications that do not use a launcher (e.g. most terminal-only applications)

---

### Post by Frogs Hair on 2012-09-15
This method will create a list in your home folder, but I don't see third party applications.  listed.[http://askubuntu.com/questions/137982/how-to-get-a-list-of-installed-software-packages](http://askubuntu.com/questions/137982/how-to-get-a-list-of-installed-software-packages)

The method above will display all though.

---

### Post by MadMonkey1966 on 2012-09-15
> **hakermania said:**
> I guess the best thing you have to do is to right click on the Dash Home, select Applications and choose under 'Filter Results' "All". Under the Installed section you will find all of you applications.

If you want a cop-able list, I guess you can save the output of 
```

ls /usr/share/applications/

```Note though that the above will not list the applications that do not use a launcher (e.g. most terminal-only applications)

Many thanks for that, your a star (as everyone is here in the Forums). 

That is exactly what i need.....i can get started now.

Many Thanks again \\:D/

---

### Post by JKyleOKC on 2012-09-15
You can do this to get a complete list: ```
dpkg --get-selections > installed-software
```It will create a file "installed-software" in your home directory, that you can copy to a flash drive. After you do the clean install, issue the same command on the new system, then compare the original file and the new one to determine what packages on your old system are not yet present on the new.

This is much easier than trying to work through a directory listing, and has the added benefit of giving you the package names instead of the program names (which are often different).

---

### Post by josephmills on 2012-09-15
I know that this is solved but I also have this trouble sometimes and this is what I do 

Old Computer
make a list of all things installed 
```
dpkg-query -l | awk '{print $2}' > ~/installlist.txt
```

move the list over to new computer 
I use paste.ubuntu.com sometimes
```
cat ~/installlist.txt | pastebinit
```

get the link and off to the 
New Computer 

take the list and save it to your home folder then 
Run a while loop to install everything on the list 

```

cat ~/installlist.txt | while read -r line;do sudo apt-get -y install $line; done

```

that is it

---

### Post by Lars Noodén on 2012-09-15
> **JKyleOKC said:**
> You can do this to get a complete list: ```
dpkg --get-selections > installed-software
```It will create a file "installed-software" in your home directory, that you can copy to a flash drive. After you do the clean install, issue the same command on the new system, then compare the original file and the new one to determine what packages on your old system are not yet present on the new.

This is much easier than trying to work through a directory listing, and has the added benefit of giving you the package names instead of the program names (which are often different).

That can be easily restored:

```

sudo dpkg --set-selections < installed-software
sudo apt-get dselect-upgrade

```

get/set selections will give you the whole nine yards.  If you just want to see what you've added, then [deborphan](http://manpages.ubuntu.com/manpages/precise/en/man1/deborphan.1.html) can help.

```

deborphan --all-packages --no-show-section | sed -e 's/:.*$//'

```

---

