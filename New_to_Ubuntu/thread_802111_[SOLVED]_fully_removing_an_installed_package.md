---
title: "[SOLVED] fully removing an installed package"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by HunterSBuntu on 2008-05-21
I installed the xubuntu-desktop package and I'm having issues getting it to work.

If I can't get it worked out I'd like to fully remove everything that package installed, how would I do that?  

When I mark the xubuntu-desktop package for removal in Synaptics it says it's only gonna free up 40k of space, yet when I installed it it installed 84 files and several hundred MB.

How can I get an umbrella package like this to remove everything it installed?

---

### Post by N.N. on 2008-05-21
If you used aptitude to install the package, you can just issue the following command in a terminal to remove the xubuntu-desktop package and everything that was installed with it: ```
sudo aptitude remove xubuntu-desktop
```

However, if you installed it from Synaptic or with apt-get, you'll have to specify the names of all the packages that are orphaned by removing xubuntu-desktop. See the following link if you're using Ubuntu: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome). If you are using Kubuntu, see the following link: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde).

---

### Post by NilsE on 2008-05-21
Did you use the "mark for removal" or the "mark for complete removal" option?  The second should remove everything including config files.

---

### Post by alienexplorers on 2008-05-21
Mark for complete removal does not remove all orphaned files.  It only removes completely the file selected.  If you don't know all the files that were loaded when you added the software you are out of luck on getting them all to delete.

---

### Post by HunterSBuntu on 2008-05-21
I'm pretty sure I did 'mark for complete removal' and when I hit Apply it pops up the message box which shows you what is gonna be removed and it only lists the high level xubuntu-desktop package without all the sub packages that were installed.

I'll check again tonight when I get home from work.

Thanks everyone.

---

### Post by HunterSBuntu on 2008-05-21
> **alienexplorers said:**
> Mark for complete removal does not remove all orphaned files.  It only removes completely the file selected.  If you don't know all the files that were loaded when you added the software you are out of luck on getting them all to delete.

That's what I figured.

I gotta say that's not really very user friendly or intuitive, I would think if you uninstall something it should remove everything that it brought with it.

---

### Post by N.N. on 2008-05-21
> **HunterSBuntu said:**
> That's what I figured.

I gotta say that's not really very user friendly or intuitive, I would think if you uninstall something it should remove everything that it brought with it.

Certain interfaces to the package manager, such as aptitude, have this feature. See my previous post. For more information on the subject see the following blog post: [http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/).

---

### Post by soapytheclown on 2008-05-21
> **N.N. said:**
> Certain interfaces to the package manager, such as aptitude, have this feature. See my previous post.

i think what hes looking for is a gui way of doing things, which does make sense to be fair, currently, any packages i want to install i have to find in synaptic then opena terminal then aptitude install them, a new feature should use aptitude by default in the synaptic synaptic gui i reckon.

---

### Post by drs305 on 2008-05-21
> **alienexplorers said:**
> Mark for complete removal does not remove all orphaned files.  It only removes completely the file selected.  If you don't know all the files that were loaded when you added the software you are out of luck on getting them all to delete.

You can remove orphaned files by installing deborphan via synaptic or:
```
sudo aptitude install deborphan
```
Run the following command to see the orphaned packages:
```
deborphan
```
Then run this command to remove them:
```
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by wdaniels on 2008-05-21
I'm not sure about the GUI ways but:

```
sudo apt-get autoremove
```

...should remove any remaining packages that were automatically installed as dependencies.

---

### Post by hyper_ch on 2008-05-21
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Read in the "Remove Xubuntu" section.

---

### Post by HunterSBuntu on 2008-05-21
> **soapytheclown said:**
> i think what hes looking for is a gui way of doing things, which does make sense to be fair, currently, any packages i want to install i have to find in synaptic then opena terminal then aptitude install them, a new feature should use aptitude by default in the synaptic synaptic gui i reckon.


Yeah, I was sort of hoping for a GUI way of doing it but I'm getting pretty handy with the command line so I'll check out aptitude and and deborphan as well.

I found another post about wanting to remove Xubuntu and it links to a page with a complete list of packages to remove so it should be all good.

As always, I'm amazed and impressed by how helpful (and fast) everyone on the forums are.  Thanks a lot.

---

### Post by erginemr on 2008-05-21
> **hyper_ch said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Read in the "Remove Xubuntu" section.

Hey, I was going to propose that one! ;)

Yet another way is to check out Synaptic. There should be an item to show the history of installed packages in the Synaptic menu.

---

