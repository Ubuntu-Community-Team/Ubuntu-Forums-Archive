---
title: "Repeatedly getting the same error"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by Keshav2050 on 2012-01-27
After typing the command 'sudo apt-get update', I am regularly getting an error saying:

'[B]Reading package lists... Done
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/B]'

for a different error sue to which I wasn't able to download anything from software center once I got a solution to type:

sudo rm /var/lib/apt/lists/* -vfand then 
sudo apt-get update

It worked and I did the same for the error mentioned at the starting, it worked and I didn't get the error after typing the above commands but I am regularly getting the same error whenever I open the computer, what should I do, does it always happen, should I change the way of removing error, can anyone please tell me what to do? Or should I use the same method. Why is the same error repeatedly coming? once I always used to get 

**[**
**"**W: GPG error: [http://security.ubuntu.com]("http://security.ubuntu.com/")  oneiric-security Release: The following signatures were invalid: BADSIG  40976EAF437D05B5 Ubuntu Archive Automatic Signing Key  <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/")  oneiric Release: The following signatures were invalid: BADSIG  40976EAF437D05B5 Ubuntu Archive Automatic Signing Key  <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/")  oneiric Release: The following signatures were invalid: BADSIG  16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key  <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/")  oneiric-updates Release: The following signatures were invalid: BADSIG  40976EAF437D05B5 Ubuntu Archive Automatic Signing Key  <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.**"**
**]**

but now I'm not.

---

### Post by ajgreeny on 2012-01-27
Here's two possible answers.  I have never had the problem so I don't know which is the correct answer for you, but it looks from the second post to be a combination of both things;  first get rid if the old lists and keys, then get the correct new keys.
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)
[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

---

### Post by Keshav2050 on 2012-01-28
I got :
[B]# mv lists lists.old 
mv: cannot move `lists' to `lists.old/lists': Directory not empty [/B]

by trying the first method in the first link.

---

### Post by Keshav2050 on 2012-01-28
May be the error is not that frequent, it may come once in a week or so.

---

### Post by Keshav2050 on 2012-01-29
Recently I got


[B]W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
[/B]

---

### Post by kazztan0325 on 2012-01-29
Hi Keshav2050,

I usually use **'Y PPA Manager'** to try to import missing GPG keys or to fix GPG BADSIG errors.

**'Y PPA Manager'** PPA is here:
[https://launchpad.net/~webupd8team/%2Barchive/y-ppa-manager]("https://launchpad.net/~webupd8team/%2Barchive/y-ppa-manager")

And the article about the tool is here:
[http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html]("http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html")

I hope this would help you resolve the issue.

---

### Post by Keshav2050 on 2012-01-30
Thanks you, but I think It's not working or I didn't know how to use it, I tried to remove errors from advanced but I'm getting

[B]Reading package lists... Done
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[/B]

---

### Post by kazztan0325 on 2012-01-31
Oh, really?

Hmmmm..., it is very strange...
'Y PPA Manager' works well for me...

Sorry, I have no other ideas at present.

---

### Post by Keshav2050 on 2012-01-31
Today I'm getting the error as:

[B]Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[/B]

---

### Post by Keshav2050 on 2012-02-01
Can anyone please tell me what has happened or how to solve the problem?

---

### Post by Keshav2050 on 2012-02-04
When I use the following commands to solve the problem
# sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update

I get 
**mv: cannot move `lists' to `lists.old/lists': Directory not empty**
after the command **# mv lists lists.old**

What should I do?

---

### Post by oldos2er on 2012-02-04
If lists.old already exists, move it somewhere else, e.g. your home folder ```
mv lists /home/user/lists.old
```

---

### Post by Keshav2050 on 2012-02-05
Thank you very much again.
There are no errors.

First when I tried

**mv lists /home/user/lists.old**

I got

**mv: cannot move `lists' to `/home/user/lists.old': No such file or directory**

so I tried the command

**mv lists /home/user**

a new folder called **user** has been created in my home folder, and another folder **lists** in '/var/lib/apt', now since there another folder 'lists' has been created in it, can I delete the **user** in **home** folder?

---

### Post by oldos2er on 2012-02-05
You need to replace 'user' with your own user account name.

---

### Post by Keshav2050 on 2012-02-07
Oh! Sorry I just typed 'user' and not actual user account name, so what should I do, paste all that is there in user which has been created(accidentally), in a new folder 'lists.old' which I have to create(which may have happened if I did as you told) in the home folder(and remove/delete newly created 'user')? Or can I just delete the newly created folder 'user'?

---

### Post by oldos2er on 2012-02-07
I would just delete the new 'user' folder (you will have to do so as root), then run through the commands in post #11 again.

---

### Post by Keshav2050 on 2012-02-09
since you said to do as root I used the command

**sudo -i**

then I went to home directory by typing **cd /home**, then I typed **ls** to view the contents, then I tried to delete the new folder 'user' which I was tying to delete by typing 
**rm user**
then I got **rm: cannot remove `user': Is a directory**. Did I do any mistake again?

---

### Post by oldos2er on 2012-02-09
To remove a directory with rm, you need to use the -r option ```
rm -r user/
``` from within the /home directory. ```
man rm
``` will give you more info.

---

### Post by Keshav2050 on 2012-02-10
Thank you very much for your help, what should I do with **lists.old** in **/home/user**, can I delete it? Or should I leave it there, may be it can be of some use for us or for the computer to work properly?

---

### Post by oldos2er on 2012-02-10
If you're no longer getting APT (package manager) errors, it's safe to delete lists.old, it is not needed.

---

### Post by Keshav2050 on 2012-02-11
Thanks again, I just got a doubt, I read in some link that the method mentioned in post #11 worked only once, may be because **lists.old** was not present before when it was tried for the first time, so from second time onwards the method didn't work, so should I try to delete **lists.old** in **/var/lib/apt **(if you say it isn't of any of any use) so that I can use the commands in post #11 if I get any gpg or badsig error then if I'm asked to repeat the commands in post #11(may or may not be exactly like in post #11) I can use them and delete **lists.old** again?

---

### Post by oldos2er on 2012-02-11
I would only use the commands in post #11 for BADSIG errors; they may not be applicable to other gpg errors.

I think I answered your question in post #12. If **lists.old** already exists, then you will need to move or delete it to run **mv lists lists.old** successfully. You could change the name to something else, say **mv lists lists.bak** instead. It's up to you.

---

### Post by Keshav2050 on 2012-02-12
:smile:Thanks for helping.

---

