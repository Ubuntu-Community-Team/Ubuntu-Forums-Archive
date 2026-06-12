---
title: "local directory on hard drive as a repository?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by nutpants on 2008-11-09
how do i add a local directory on hard drive as a repository for synaptic?

nutz

---

### Post by niccholaspage on 2008-11-09
I want to do the same thing.

---

### Post by nutpants on 2008-11-09
i found these very old instructions...

The line in my sources.list looks like this:

deb file:///data/Downloads-Archives/packages/ ./

Don't forget the ./ at the end (tells to apt-get and Synaptic to look right here for packages and also for the file Packages.gz) After saving the file, hit the reload button in Synaptic. But it will complain that it does not find Packages.gz in your local repo, because for a repo that is also neeeded.

So each time after you download/delete packages in this repo directory, you first need to cd to your repo dir (/data/Downloads-Archives/packages/ in my case), and then run this command from the console:

sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

This will update your Packages.gz file. If you hit Synaptic 'reload' button now, the packages will appear in Synaptic, and you can install them.

but i need  dpkg-dev for 
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

and it is not showing up in synaptic 
( which i am having trouble updating in intrepid x64 the whole reason for this exercise)

so i dont know if this works
nutz

---

### Post by caljohnsmith on 2008-11-09
Here is a method that has worked for me that you could use:
[LIST=1]
[*]Create a local repository directory:
```
mkdir ~/Local_repository
```
[*]Put all downloaded .deb files in that Local_repository folder
[*]Run:
```
dpkg-scanpackages ~/Local_repository /dev/null > ~/Local_repository/Packages
```
[*]Add following line to /etc/apt/sources.list:          
```
deb file:///home/<username>/Local_repository /
```
And replace <username> with your username. 
[*]Last run:
```
sudo apt-get update
```
[/LIST]
And all the .deb packages in your Local_repository directory should show up in Synaptic. Let me know if that works for you too.

---

