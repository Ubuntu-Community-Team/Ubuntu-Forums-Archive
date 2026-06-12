---
title: "files have a lock picture"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by mlempenau on 2014-06-26
I switched from 13.10 to 14.04 not too long ago.  I had it set up where when I imported a file from another computer I had full edit control.  Now the lock pic is there.  But I don't remember what I did to get rid of the lock pic.  Please remind me.

---

### Post by nerdtron on 2014-06-26
The lock on the icon means you are not the owner or you don't have permissions on that file. Your upgrade might have caused this.

To change the ownership, open a terminal and go to the folder in question:

```
cd /folder/with/locks
sudo chown -R user:user *
```

Change user with you username. Also don't do this on the the system directories, just use it on you own files.

---

### Post by mlempenau on 2014-06-26
How do I find my correct user name?  I thought it was mlempenau, but this didn't work.  So I tried Michael Lempenau but because it's two words it didn't take it.  


mlempenau@mlempenau1404:~$ cd /home/mlempenau/Documents/BlueCross/Drugs/2014
mlempenau@mlempenau1404:~/Documents/BlueCross/Drugs/2014$ ls
Apr2014  Feb2014  Jan2014  Jul2014  Jun2014  Mar2014  May2014
mlempenau@mlempenau1404:~/Documents/BlueCross/Drugs/2014$ cd /home/mlempenau/Documents/BlueCross/Drugs/2014/Jul2014
mlempenau@mlempenau1404:~/Documents/BlueCross/Drugs/2014/Jul2014$ ls
Jul2014.pdf  Jul2014.pfl
mlempenau@mlempenau1404:~/Documents/BlueCross/Drugs/2014/Jul2014$ sudo chown -R user:mlempenau *
[sudo] password for mlempenau: 
chown: invalid user: &#8216;user:mlempenau&#8217;
mlempenau@mlempenau1404:~/Documents/BlueCross/Drugs/2014/Jul2014$ sudo chown -R user:Michael Lempenau *
chown: invalid user: &#8216;user:Michael&#8217;
mlempenau@mlempenau1404:~/Documents/BlueCross/Drugs/2014/Jul2014$

---

### Post by deadflowr on 2014-06-27
You ran the command with user:mlempenau?
Do it with
mlempenau:mlenpanau

The first entry is the owner, the second is the group.
So what you did was enter the owner name "user"  and your actual username as the group name.

But this is overall a band-aide.
The real solution will be figuring out the file sharing method you used before.

---

### Post by mlempenau on 2014-06-27
That worked ... Thanks

Now if I could only remember what I did before.  Your correct, this is a band-aid.

---

