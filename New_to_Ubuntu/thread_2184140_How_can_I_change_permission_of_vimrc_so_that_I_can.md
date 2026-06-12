---
title: "How can I change permission of vimrc so that I can write to it?"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by zeynel2 on 2013-10-27
Now ```
$ [COLOR=#3A3A3A]:e $MYVIMRC
``` opens a read only version.[/COLOR]

---

### Post by apollothethird on 2013-10-27
> **zeynel2 said:**
> Now ```
$ [COLOR=#3A3A3A]:e $MYVIMRC[/COLOR]
```[COLOR=#3A3A3A] opens a read only version.[/COLOR]

Your code block suggest that you're at a command prompt.  If you're at a command prompt, the ":e" command should give you an error message.

Which application are you running?  I can test the application and give you more details.

In the meantime will you give us the output of these commands:

```

$ echo  $MYVIMRC
$ ls -l  $MYVIMRC

```

Those commands are executed at the shell prompt.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by zeynel2 on 2013-10-27
I am sorry, I was actually in vim and opened the file with [COLOR=#3A3A3A][FONT=Ubuntu Mono]:e $MYVIMRC but could not write to it. That's why I was asking how to change the permission in vim so that I can write to it.[/FONT][/COLOR]

---

### Post by apollothethird on 2013-10-28
> **zeynel2 said:**
> I am sorry, I was actually in vim and opened the file with [COLOR=#3A3A3A][FONT=Ubuntu Mono]:e $MYVIMRC but could not write to it. That's why I was asking how to change the permission in vim so that I can write to it.[/FONT][/COLOR]

If you tell us the results you get when you type in the commands I gave you in my first reply we could most likely easily identify your problem and tell you exactly what to do to resolve the issue.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zeynel2 on 2013-10-28
Here are the results:

```

a@b:~$ echo $MYVIMRC

a@b:~$ ls -l $MYVIMRC
total 60
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Desktop
drwxr-xr-x 10 a a 4096 Oct 27 15:17 Documents
drwxr-xr-x  2 a a 4096 Oct 27 12:10 Downloads
drwx------  5 a a 4096 Oct 27 15:14 Dropbox
-rw-r--r--  1 a a 8445 Oct 19 15:21 examples.desktop
drwxrwxr-x  2 a a 4096 Oct 19 15:45 leiningen
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Music
drwxrwxr-x  6 a a 4096 Oct 19 17:30 my-new-project
drwxr-xr-x  2 a a 4096 Oct 27 12:10 Pictures
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Public
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Templates
drwxrwxr-x  2 a a 4096 Oct 22 19:34 Ubuntu One
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Videos
a@b:~$
```

---

### Post by Impavidus on 2013-10-28
Usually your vimrc is in a file called **.vimrc**, which can be found automatically by vim. I don't think vim checks for the environment variable MYVIMRC, but maybe you had something special in mind.

Vim understands environment variables and the command **:e $MYVIMRC** will cause it to read the environment variable **MYVIMRC**, which may contain the string **foo.txt**, and then vim will open the file **foo.txt** for editing. In your case it seems that the environment variable **MYVIMRC** doesn't exist, in which case vim will open the file **$MYVIMRC** (yes, the string you gave, including the dollar sign) for editing in the current directory. If the file exists but you don't have write permission for the file or if the file doesn't exist and you don't have write permission in the current directory, the file will be read-only.

---

### Post by BrunoLotse on 2013-10-28
Hi:) execute this command ```
chmod 600 ~/.vimrc
```  Now you should be able to open it in write mode.Cheers, Bruno

---

### Post by apollothethird on 2013-10-28
> **zeynel2 said:**
> Here are the results:

```

a@b:~$ echo $MYVIMRC

a@b:~$ ls -l $MYVIMRC
total 60
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Desktop
drwxr-xr-x 10 a a 4096 Oct 27 15:17 Documents
drwxr-xr-x  2 a a 4096 Oct 27 12:10 Downloads
drwx------  5 a a 4096 Oct 27 15:14 Dropbox
-rw-r--r--  1 a a 8445 Oct 19 15:21 examples.desktop
drwxrwxr-x  2 a a 4096 Oct 19 15:45 leiningen
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Music
drwxrwxr-x  6 a a 4096 Oct 19 17:30 my-new-project
drwxr-xr-x  2 a a 4096 Oct 27 12:10 Pictures
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Public
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Templates
drwxrwxr-x  2 a a 4096 Oct 22 19:34 Ubuntu One
drwxr-xr-x  2 a a 4096 Oct 19 15:35 Videos
a@b:~$
```

Hi, Zeynel2.

Thanks for giving us this information.  The problem you were experiencing had nothing to do with the permissions of your vimrc file.  From the output, you were trying to access and write to something that didn't exist.

Try using the ":e" command to actually create and write to the file you wish to write to (i.e. :e .vimrc).  You won't have to bother with the permissions.  The permissions will automatically be set when you create the file.  Again, the command you were using was not performing what you expected.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by BrunoLotse on 2013-10-28
Not true. 
From the provided output we have no idea wether .vimrc exists or not on the system. Most probably it does exist. We need the output of hidden, i.e. dot files. Search for hidden files and you most probably see .vimrc with read only permissions. Cheers.Bruno

---

### Post by Impavidus on 2013-10-28
At no point the OP has referred to .vimrc. He has only referred to $MYVIMRC, which is an undefined variable. It's very unlikely he actually wanted to create a file with the name $MYVIMRC, but that is what he told vim to do and what is what didn't work. Most likely he wanted to write to the file ~/.vimrc. So the less relevant question is: Does the OP have write permission in the current directory? The more relevant question is: How does one make the environment variable MYVIMRC point to the file ~/.vimrc? This can be done by putting it in ~/.bashrc, but I don't think he actually needs it. Vim will check ~/.vimrc by default. Just refer to it by its name and forget about the MYVIMRC, unless you had something special in mind.

---

### Post by zeynel2 on 2013-10-28
> **BrunoLotse said:**
> Hi:) execute this command ```
chmod 600 ~/.vimrc
```  Now you should be able to open it in write mode.Cheers, Bruno

Thanks, this worked, but I had to add sudo: ```
sudo chmod 600 ~/.vimrc
```.

---

### Post by apollothethird on 2013-10-28
> **zeynel2 said:**
> Thanks, this worked, but I had to add sudo: ```
sudo chmod 600 ~/.vimrc
```.

Hi, Zeynel.  Glad you got your issue resolved.

By the way, as I mentioned before, you didn't have to change your ~/.vimrc for access permission.  You already had access just by actually creating the file.

Finally, if your issue is resolved, please consider using the system tools to make the thread as SOLVED.  This would be an appreciated contribution back to the community.  Others with a similar question can easier find their solution.

Have a nice day!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zeynel2 on 2013-10-28
Thanks, for the help. I read my question, and indeed it was too terse and confusing. I was trying to follow the instructions here [http://vim.wikia.com/wiki/Open_vimrc_file#Opening_vimrc](http://vim.wikia.com/wiki/Open_vimrc_file#Opening_vimrc) to open .vimrc, that's why ```
[COLOR=#3A3A3A]:e $MYVIMRC[/COLOR]
```[COLOR=#3A3A3A] was in my question.[/COLOR]

---

### Post by apollothethird on 2013-10-28
> **zeynel2 said:**
> Thanks, for the help. I read my question, and indeed it was too terse and confusing. I was trying to follow the instructions here [http://vim.wikia.com/wiki/Open_vimrc_file#Opening_vimrc](http://vim.wikia.com/wiki/Open_vimrc_file#Opening_vimrc) to open .vimrc, that's why ```
[COLOR=#3A3A3A]:e $MYVIMRC[/COLOR]
```[COLOR=#3A3A3A] was in my question.[/COLOR]

Zeynel2.  It appears, after reading your link and running local test, the string variables are expanded when in the vim environment.  That takes us back to my original assessment (as a few others has mentioned), your problem was in that you didn't have a the $MYVIMRC variable set to anything.

Your link says this is set automatically.  However, it appears that, this isn't so (the automatic set of the variable) in every distribution... as in the case of the Ubuntu version you and I are apparently running.

You can remedy this by manually setting the MYVIMRC in your .bashrc file.  After the setting of the variable, it'll work for you just as it does in the link you posted.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zeynel2 on 2013-10-29
> **Impavidus said:**
> Vim understands environment variables and the command **:e $MYVIMRC** will cause it to read the environment variable **MYVIMRC**, which may contain the string **foo.txt**, and then vim will open the file **foo.txt** for editing. In your case it seems that the environment variable **MYVIMRC** doesn't exist, in which case vim will open the file **$MYVIMRC** (yes, the string you gave, including the dollar sign) for editing in the current directory.

Yes, this is what happens. How do I set $MYVIMRC to open .vimrc? :e echo $MYVIMRC as explained here [http://stackoverflow.com/a/8977682/215094](http://stackoverflow.com/a/8977682/215094) does not seem to work.

---

### Post by BrunoLotse on 2013-10-29
Hi :)You don't have to set MYVIMRC in your environment. vim is able to figure it out on its own. Try this. Open some other file on your system - like  ```
vim  ~/my_test_file.txt
``` When the file is on type ```
:e $MYVIMRC
``` Vim should open config file .vimrc set on your system.Cheers,Bruno

---

### Post by Impavidus on 2013-10-29
I would have sworn it didn't work yesterday (I have got a .vimrc). Maybe I made a typo.

---

### Post by BrunoLotse on 2013-10-29
All well that ends well :)Here you will find a good example of vimrc file [http://vim.wikia.com/wiki/Example_vimrc](http://vim.wikia.com/wiki/Example_vimrc)Try learn and use vi. It's worth it. Cheers, Bruno

---

### Post by zeynel2 on 2013-10-30
> **BrunoLotse said:**
> Hi :)You don't have to set MYVIMRC in your environment. vim is able to figure it out on its own. Try this. Open some other file on your system - like  ```
vim  ~/my_test_file.txt
``` When the file is on type ```
:e $MYVIMRC
``` Vim should open config file .vimrc set on your system.Cheers,Bruno

Thanks, but when I do this exactly as instructed, vim opens a new file named $MYVIMRC; it does not open my existing .vimrc file.

---

### Post by BrunoLotse on 2013-10-30
Hi:) This is strange. You mentioned that you need to apply sudo when changing .vimrc permissions. This is also fishy. It looks like some other user is owing your config file. Try to figure out what user it is. ```
\ls -l ~/.vimrc 
```When you execute this do you see your username?Cheers,Bruno

---

### Post by zeynel2 on 2013-10-31
Hi, Bruno, thanks for the help. This is what I see:

```
a@b:~$ \ls -l ~/.vimrc
-rw------- 1 root root 964 Oct 30 06:07 /home/a/.vimrc
a@b:~$ 
```

---

### Post by BrunoLotse on 2013-10-31
Hi:) Yep, we see that file ~/.vimrc belongs to root. But it should belong to you, i.e. user a. So you have to change ownership of the file```
sudo chown a:a /home/a/.vimrc
```You are changing root to user a. Run ls -l ~/.vimrc, make sure that root is gone and a is in place and then run vim. When vim is running execute ```
:e $MYVIMRC
```vim should open your ~/.vimrc config file which you can edit.Cheers, BrunoP.S. You're welcome:)

---

### Post by Impavidus on 2013-10-31
And to prevent it from becoming root-owned again, never edit your .vimrc from vim when running as root. I suspect that's what happend.

---

### Post by zeynel2 on 2013-10-31
> **Impavidus said:**
> And to prevent it from becoming root-owned again, never edit your .vimrc from vim when running as root. I suspect that's what happend.

Can you explain this? I am still very confused about the file management. Why would it run vim as root?

---

### Post by zeynel2 on 2013-10-31
Great, thanks again, this is now working.

---

### Post by Impavidus on 2013-10-31
Maybe you thought: Let's change this root-owned file, and then typed **sudo vim <filename>**. Then you thought: I want to change my .vimrc, so you typed **:e $MYVIMRC**. Then you saved your .vimrc and it would have been root-owned, as vim was running as root.

I've seen many tutorials telling people to work with certain root-owned files, probably because they are always there. I think it's wiser to stay away from them when following tutorials. You don't know yet what you're doing.

---

### Post by apollothethird on 2013-11-02
> **zeynel2 said:**
> Great, thanks again, this is now working.

Hi, Zeynel2.

We are glad you have your issue resolved.

Please consider that you can actually give back to the community by marking this issue as solved.  It'll save out time when reviewing unsolved issues trying to help users who are still trying to get a resolution.  It'll also help others who have a similar issue to zoom in on the threads that have been resolved.

You can mark it solved by clicking on "Tread Tools" > "Mark this thread as solved".

Thanks again for any consideration on this.

We are always glad to help!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

