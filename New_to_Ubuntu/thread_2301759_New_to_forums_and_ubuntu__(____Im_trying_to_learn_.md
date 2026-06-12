---
title: "New to forums and ubuntu : (    Im trying to learn shell..  what am I doing wrong"
date: 2015-11-05
forum: New to Ubuntu
---

### Post by james_4 on 2015-11-05
lulwat@lulwat:~$ pwd
/home/lulwat
lulwat@lulwat:~$ cd ..
lulwat@lulwat:/home$ cd ~
lulwat@lulwat:~$ ls
Desktop    Downloads         Link to WIN TO NIX NIX TO WIN  Pictures  Templates
Documents  examples.desktop  Music                          Public    Videos
lolwat@lulwat:~$ cd ~/downloads
bash: cd: /home/lulwat/downloads: No such file or directory
lolwat@lulwat:~$ cd ~/downloads/
bash: cd: /home/lulwat/downloads/: No such file or directory
lulwat@lulwat:~$ 


I’m trying to learn how to get around in shell..  right now I'm having issues navigating to the downloads folder.. 
I’m just trying out what I just learned on codecademy

---

### Post by howefield on 2015-11-05
Downloads should be capitalised, you do not have a "downloads" folder.

Look at the result of your ls command..

---

### Post by james_4 on 2015-11-05
wow....    :) thanks.  Never would have thought its case sensitive..

---

### Post by Lars Noodén on 2015-11-05
There's also tab completion, if you haven't found that yet.  Start typing as normal and then press tab when you what you have so far is unique.  e.g.

```

cd ~/Doc<tab>
cd ~/Dow<tab>

```

You get used to it very quickly and it saves on typing.

---

### Post by ajgreeny on 2015-11-05
Tab completion will also overcome another of the problems that you may come across with files and folders with spaces in their names.

For these files you have to use an escape character in terminal, ie either quotation marks around the full pathway, or a backslash before the space, so a folder called **rock music** will have to be typed as **rock\ music** or **"rock music"**.  Type rock then hit tab and the terminal will fill in the rest for you and escape the space for you with a backslash; if there is more than one match tab x2 will show all the matching options.

---

