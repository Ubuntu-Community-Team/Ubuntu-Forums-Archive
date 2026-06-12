---
title: "creating tarball of /home or /home/username?"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2012-03-06
I want to migrate my settings and files (i.e., in /home) from my OLD computer to a NEW computer. Both run 10.04 and both have exactly the same user name and password.

My question is do I make a tarball of the entire /home directory which of course contains /myusername directory, or only the latter?

In either case, the instructions I have say to sign in as root. As I understand it, Ubuntu does not contain a root option, rather one uses sudo as needed.

So my concern has to do with the privileges necessary for creating, transferring, and unzipping the tarball. So how do I sign in to do each of these, or do I just use sudo in all cases?

Finally, when I get the tarball to the NEW computer, where should it be located while the unzipping is going on. Specifically, should it be in /home or /home/myusername?

If the former, should the existing subdirectory of /myusername be renamed to "make room" for the unzipped data complete with the /myusername directory (since the data is a tarball of /myusername on the OLD computer)?

Hope this isn't confusing, but happy to clarify if needed. Thanks.

---

### Post by TeoBigusGeekus on 2012-03-06
Don't make a mess out of a simple job. Root has nothing to do with your home folder. Either
```
tar cvzf backup_of_home_folder.tar.gz ~/
```
or just copy your home folder to an external hd and you're done.

---

### Post by Odyssey1942 on 2012-03-06
In your code suggestion, is the directory to be tarballed (tilde in front of slash) the /home directory? or the /myuser directory within the /home directory? I will need to know this when it comes time to extract the tarball.

Perhaps I should be asking this in the Newbie forum (as I am very much a noob), but though it might make more sense here because I have Ubuntu.

I am asking these questions because I am not finding this a simple job to complete at all, want to understand what I am doing, and will very much appreciate answers to those questions. Thanks.

---

### Post by Derek Karpinski on 2012-03-06
> **Odyssey1942 said:**
> In your code suggestion, is the directory to be tarballed (tilde in front of slash) the /home directory? or the /myuser directory within the /home directory? I will need to know this when it comes time to extract the tarball.
 
Perhaps I should be asking this in the Newbie forum (as I am very much a noob), but though it might make more sense here because I have Ubuntu.
 
I am asking these questions because I am not finding this a simple job to complete at all, want to understand what I am doing, and will very much appreciate answers to those questions. Thanks.
 
Answer your own question: :)
 
```
cd ~/
 
pwd
```

---

### Post by Odyssey1942 on 2012-03-06
Maybe I should start over and give some background. I am in a terrible muddle. Here is the history:

in old computer I ran:
```
sudo tar /opt/username120305.tar.gz /home
``` (put into opt to keep from creating the tarball within the directory being zipped) then from within /opt
```
sudo scp username120305.tar.gz /home@192.168.0.104
```which failed with error message: "permission denied, please try again" (i.e., would not accept my password [which I know is correct and retried several times]), then
```
sudo scp username120305.tar.gz /username@192.168.0.104
```which worked.

Then in /home at the new computer, I renamed /username /username2, moved username120305.tar.gz into /home and unpacked it.

Now when I boot up new computer, I put in my password at login as normal, but then get the following three error messages on a blank desktop (color only, no icons)

1)Could not update ICEauthority file /home/username/ICEauthority
2)There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
3)Nautilus could not create the following required folders: /home/username/Desktop, /home.username.nautilus (Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.)

So my question is, can anyone see anything in the above that caused this whole process to go pear shaped?

Secondly, why do /home and /username on the new computer seem to need different passwords in order to scp the files over?

I am very much a noob at the command line, so more information rather than less will be so appreciated (I hope to learn something from all this) Thanks.

---

### Post by Odyssey1942 on 2012-03-08
Is there another unbuntuforums forum better suited to this issue?

---

### Post by georgelab on 2012-03-08
Did you get any error messages during the tarball creation? Besides it, did you change permissions for the files inside the tarball?

I prefer copying my home subdirectories then copying the home directory at all. Some hidden configuration files can cause big trouble.

---

### Post by jerome1232 on 2012-03-08
Ensure that the user has ownership of the files in it's own home. (I can't recall if scp preserves original permissions atm or not)

```
sudo chown -R $USER:$USER ~/
```

Also check that the folder hierarchy is as intended in the new home.

---

### Post by georgelab on 2012-03-08
You should also use scp -p parameter. This will retain file permissions and modification dates.

---

### Post by Odyssey1942 on 2012-03-08
Thanks for all the great questions and suggestions. For both of you, I was careful to use exactly the same username (spelling, case, etc.) and password on the new computer as on the old. Is this sufficient or do I need to take additional measures?

Georgelab, all the below is for you, and I will make a separate set of questions for Jerome.

There were no error messages during the tarball creation. 

> Besides it, did you change permissions for the files inside the tarball? I did not change permissions before creating the tarball or after. I assumed that they would be the same after making the tarball, but did I need to use a tar argument that specifically retained exactly the permissions that existed on the old computer?

> I prefer copying my home subdirectories than copying the home directory at all.I want to understand this in some detail because I think my lack of understanding of /home and /home/user, especially at the unpacking end may be the source of my problem.

Do you mean that you like to copy /home/user when you say subdirectories, and by that I understand you to mean that you are not copying the /home directory at all, just /user as a subdirectory of /home. Or do you mean something else?

Finally for Georgelab, once the tarball is created, which as I understand it, kind of creates a wrapper around the files inside, can the scp command affect the permissions? Thanks.

---

### Post by Odyssey1942 on 2012-03-08
Jerome,

> Ensure that the user has ownership of the files in it's own home. (I can't recall if scp preserves original permissions atm or not) I don't know how to do this. Your additional guidance will be appreciated.

Code:
```
sudo chown -R $USER:$USER ~/
``` I am not having much success with this. In your example, should I substitute my username (robert) for USER, so that it becomes ```
sudo chown -R $robert:$robert ~/
```? 

When I try that, it returns:
> chown: cannot access '/home/robert/.gvfs Permission denied.

Same result if I just copy your code and try that. 

> Also check that the folder hierarchy is as intended in the new home. Afraid that I am a genuine beginner here, don't understand what I should do, and will appreciate your patience and more elaborate guidance. Thanks.

---

### Post by jerome1232 on 2012-03-08
Copying the command exactly is correct (that command made sure the home folder was owned by your user), the .gvfs is a special file and it's normal to get permision denied, the command worked.


The second half meant, pop open your file browser and take a look to make sure you didn't accidentally put the folders in a subfolder under ~/ or you accidentally put them in /home. If all of your files are under ~/ and it's still not working then I'm out of quick fix checks.

---

### Post by kevdog on 2012-03-08
I'm scratching my head why you are not using rsync to do this job, but what do I know.

---

### Post by Odyssey1942 on 2012-03-08
I need to explain that I first tried that on the old computer to see what the correct alternative was, and when it knocked me back, I did not try it on the new computer.

I have done so now, and when I put in my password, it replied:
Sorry, try again. So I tried again. Same result. Then I tried a third time. This time the response was:

"Sudo.: 3 incorrect password attempts"

returned me to the prompt.

So that is the first thing.

The second has to do with your suggestion to look in a browser (presumably on the new computer). The problem that I am trying to solve is that I am unable to open a browser, or anything at all after I login. I am just looking at an orange/brownish Ubuntu solid screen without so much as a single letter, word, or anything else on the screen, that is, after the display of three error messages which I described in the earlier post which began "Maybe I should start over and give some background."

---

### Post by Odyssey1942 on 2012-03-08
Kevdog, Sometimes a question gives rise to an aha moment. 

Maybe what I should be asking is what are the steps to transfer my user subdirectory to the new computer? In fact, I will start a new thread with that question.

---

### Post by Miljet on 2012-03-08
As was mentioned previously, you are overly complicating things by using sudo. All files within your /home/username/ belong to you and do not require root privileges to copy or move. When you use sudo to create a directory or file, that directory or file then belongs to root.

---

### Post by Odyssey1942 on 2012-03-08
Miljet, thanks for yours. That brings into focus one thing that has been puzzling me. What is the difference in Ubuntu between root and sudo? I understood that one used sudo, as needed, to become root for the operation at hand.

So why is root any different from me as a user as sudo?

Or are you saying that root is closed to users in Ubuntu, i.e., that a user cannot be root?

---

### Post by jerome1232 on 2012-03-08
> **Odyssey1942 said:**
> 
So why is root any different from me as a user as sudo?


When you use sudo, it escalates your unprivilaged user to be the same as if it were root, if you create a file using sudo, said file will be owned by root and not your own user.

When working in your own home, the files should be owned by you, thus there is no reason or need to be mucking around with sudo. (aside from the example I gave which was assuming the permissions where already messed up and was ensuring the files are owned by your user)

---

### Post by Odyssey1942 on 2012-03-08
OK, I think I have it now.

Here is the proposed solution:

```
chown robert:robert /home/robert
```

or

```
sudo chown robert:robert /home/robert
```(sudo if needed)

Thank you for your patience in this.

---

