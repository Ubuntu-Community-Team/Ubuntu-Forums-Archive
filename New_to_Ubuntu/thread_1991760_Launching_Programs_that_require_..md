---
title: "Launching Programs that require ./"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by SushiAddiction on 2012-05-30
I have had several programs that need ./ to start. I want to make a desktop launcher but have no Idea what to put in "command".
I have used a bash script that works
```
#!/bin/bash
#
cd /home/sushi/Downloads/Portable/KeyHoleTV64
./lkeyholetv
``` but I want to create a launcher (desktop or unity) I know how to create these but not what 'command' to use.
```
/home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv
```The above command does not work :( 

As you can see I have apps that don't need to be installed in /Portable/

Also I don't really understand why ./ is needed. Can someone point me in the right direction?

---

### Post by zombifier25 on 2012-05-31
./ expands to current directory. so *./lkeyholetv* expands to */home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv*, if your current directory is */home/sushi/Downloads/Portable/KeyHoleTV64*
Dunno why it shouldn't work; try typing that command in the terminal and check the output.

---

### Post by poettone on 2012-05-31
the only time that I've ever had to use "./" is when running a bash script in the directory I'm currently in. 

If you wanted to run a bash .sh script from another location or nested in another script would be to enter is as "bash script.sh" or on the command line, "sudo bash script.sh"

As far as the answer to your question, as the previous reply noted, you should include the full path to the script or set a PATH for the environment the script is being ran from.

The desktop launcher is simply a shortcut so putting bash /pathtoscript/script.sh in the launcher command window should solve your issue.

Regards,
Poettone

---

### Post by gnusci on 2012-05-31
Move all the programs to ~/bin, then you can run without ./

EDIT: Ej:

cp /home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv ~/bin/

If ~bin doesnt exits, just 

$ mkdir ~/bin

After that, you can run:

$ lkeyholetv

---

### Post by SushiAddiction on 2012-05-31
> **gnusci said:**
> Move all the programs to ~/bin, then you can run without ./

EDIT: Ej:

cp /home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv ~/bin/

If ~bin doesnt exits, just 

$ mkdir ~/bin

After that, you can run:

$ lkeyholetv
Thanks.

The problem is i would rather not use /bin/ because I use several vm's and do not want to add /bin/ as a folder in the vm.

I guessing having to use "./" e.g. 
./lkeyholetv
has something to do with permissions/security. Moving to bin would solve the problem but I don't want to do that.

EDIT> ah do you mean create a folder /home/sushi/bin ?
Would it matter if I had windows & java apps there too. All apps would be in different subdirectories.

EDIT2> found this [http://linux.about.com/od/linux101/l/blnewbie3_1_3.htm](http://linux.about.com/od/linux101/l/blnewbie3_1_3.htm)
I want to keep my apps where they are so it looks like I'm stuck with bash scripts.

---

### Post by codemaniac on 2012-05-31
> **SushiAddiction said:**
> Thanks.

The problem is i would rather not use /bin/ because I use several vm's and do not want to add /bin/ as a folder in the vm.

I guessing having to use "./" e.g. 
./lkeyholetv
has something to do with permissions/security. Moving to bin would solve the problem but I don't want to do that.

EDIT> ah do you mean create a folder /home/sushi/bin ?
Would it matter if I had windows & java apps there too. All apps would be in different subdirectories.

EDIT2> found this [http://linux.about.com/od/linux101/l/blnewbie3_1_3.htm](http://linux.about.com/od/linux101/l/blnewbie3_1_3.htm)
I want to keep my apps where they are so it looks like I'm stuck with bash scripts.


If you dont want to place your script in ~/bin as suggested , all you can do is putting the script in any directory you wish and include the directory path to the PATH variable .
```
PATH=$PATH:/data/myscripts
```

---

### Post by SushiAddiction on 2012-05-31
Thanks but it's not the scripts that I have problems with.
It's a few programs that I want to keep in
 /home/sushi/Downloads/Portable/

Each program is in it's own sub directory. I don't want to add them all to the path.
It think it's solved because the only way to run a program that is not in the path is to use 
./program
That means I stuck with bash scripts.


unless there is a way to do this
```
cd /home/sushi/Downloads/Portable/KeyHoleTV64
./lkeyholetv
```in a launcher

---

### Post by poettone on 2012-05-31
Well, I can surely understand your not wanting to do a specific thing that is so easy to do, but lets be on a more level playing field here.. How about incorporating the "cd" action in the actual bash script for the application? add a line to cd to the appropriate dir before executing anything below that.

So in your launcher enter the command to run the script and inside the script, add the cd /tothepathofthescript. 

This should do it for you.. 

!/bin/bash

cd /scriptdirectory/script.sh

Rest of the script..

To me this is splitting hairs on "how" to do the same action.. Is there a reason you don't want to add the path(as noted above) in this process?

---

### Post by SushiAddiction on 2012-05-31
It seems I'm very bad at explaining :( 
ummm
I already use scripts to execute these programs and they work.

I'm trying to find a way to do it with a desktop or unity launcher.
you know
```
gnome-desktop-item-edit ~/Desktop/ --create-new 
```but when I put
/home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv
in the command box, it does not work because that directory is not in the system path. (see command below)
```
echo $PATH
```That is why I have use ./lkeyholetv to execute it.
There are many of these and I don't want to add them all to the system path.

---

### Post by mcduck on 2012-05-31
as long as the program executable has the execute permission, simply using the full path & filename in the launcher should work just fine. So make sure your program file actually have the execute permission.

Also, if you already have scripts for launching the programs, you could simply point the launcher to the script instead of the actual executable file.

---

### Post by SushiAddiction on 2012-05-31
> **mcduck said:**
> as long as the program executable has the execute permission, simply using the full path & filename in the launcher should work just fine. So make sure your program file actually have the execute permission.

It does have permission.  Full path and filename does not work.
You can test one of the programs yourself if you are interested in watching japanese tv.
[http://www.keyholetv.jp/Viewer/Linux/](http://www.keyholetv.jp/Viewer/Linux/)
I've got 64bit

> Also, if you already have scripts for launching the programs, you could simply point the launcher to the script instead of the actual executable file.
Interesting solution. The best so far.

---

### Post by jim_24601 on 2012-05-31
Giving the full path to the executable should work whether or not it's in your $PATH. The only reason I can think of that it wouldn't is if the application itself assumes it's being run from the current directory and looks for essential files there. It's bad programming practice, but it's possible.

If you run the application using the full path from the command line, making sure you aren't in the directory that contains it (something like

```
cd
/home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv
```

), you might get some more information on why it's not working.

If it does require being run from the current directory, try
```
( cd /home/sushi/DownDownloads/Portable/KeyHoleTV64/ ; ./lkeyholetv )
```
as the command line in the launcher. This is a one-liner that spawns a sub-shell and changes the directory within it, so it should work (provided you can use a sub-shell within a launcher command, which I'm not 100% sure you can do). But it's surely worth a try.

---

### Post by SushiAddiction on 2012-05-31
Yes, thank you > I guess it must be bad programming. I was not sure before as I have seen this with several programs.

In terminal
```
/home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv

```Gives
```
Error:.//.KeyHoleTV/en_AU.so: cannot open shared object file: No such file or directory
Can not Load String Table .//.KeyHoleTV/en_US.so
```I had already tried before
```
( cd /home/sushi/DownDownloads/Portable/KeyHoleTV64/ ; ./lkeyholetv )
```but without the brackets. Neither way seems to work.

When in terminal executing from program directory using full path, it works but with an error
```
$ cd /home/sushi/Downloads/Portable/KeyHoleTV64
$ /home/sushi/Downloads/Portable/KeyHoleTV64/lkeyholetv
Error:./.KeyHoleTV/en_AU.so: cannot open shared object file: No such file or directory
```
 
Well a launcher pointing to the bash script is better than nothing.

---

### Post by dcsoldschool53 on 2012-05-31
If you want to do it from a Desktop launcher try this as the command```
/home/sushi/Downloads/Portable/KeyHoleTV64/./1keyholetv
```This should work, but test it in a terminal first without cd. There is no spaces between/./ in my example.

---

### Post by jim_24601 on 2012-05-31
There you go then. It's trying to load language resources from a hidden directory under the program directory and failing.

Did you say that you get different results when you run using the full path and when you use "./", even if you're in the program directory both times? Curious. That suggests to me that it's trying to figure out the program directory from the command line and failing somehow. I'd consider reporting a bug.

If you're in the mood to try another experiment, you could set the launcher command to
```
sh -c "cd /home/sushi/DownDownloads/Portable/KeyHoleTV64/ ; ./lkeyholetv"
```
which is effectively the same thing as the bracketed version but might work in case the launcher requires an actual executable rather than a shell command.

---

### Post by SushiAddiction on 2012-05-31
Interesting
/home/sushi/Downloads/Portable/KeyHoleTV64/./lkeyholetv
Does not work but I had no idea you could use " /./ " I'll have to remember that.

Thanks jim :) 

```
sh -c "cd /home/sushi/Downloads/Portable/KeyHoleTV64/ ; ./lkeyholetv"
```
Works perfectly.

---

### Post by jim_24601 on 2012-05-31
yay! Thanks for the feedback sushi.

---

