---
title: "Need help to Export path"
date: 2010-07-03
forum: Programming Talk
---

### Post by hoboy on 2010-07-03
I am trying to install google android.
I am following this 
[http://developer.android.com/sdk/installing.html](http://developer.android.com/sdk/installing.html).
Specifically
# On Linux, edit your ~/.bash_profile or ~/.bashrc  file. Look for a line that sets the PATH environment variable and add the full path to the tools/ directory to it. If you don't see a line setting the path, you can add one:
export PATH=${PATH}:<your_sdk_dir>/tools.
--------------------------------------------------------------------------
This is how I have set the path:
 export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools
 export PATH
In bashrc.
--------------------------------------------------------------------------
but when I run androi command I get the following error:
lucas05@lucas05-desktop:~/DEVS/android-sdk-linux_86/tools$ android
android: can't find sdkmanager.jar
when I look here /home/lucas05/DEVS/android-sdk-linux_86/tools/lib/sdkmanager.jar the file exist.

---

### Post by lkjoel on 2010-07-03
> **hoboy said:**
> I am trying to install google android.
I am following this 
[http://developer.android.com/sdk/installing.html](http://developer.android.com/sdk/installing.html).
Specifically
# On Linux, edit your ~/.bash_profile or ~/.bashrc  file. Look for a line that sets the PATH environment variable and add the full path to the tools/ directory to it. If you don't see a line setting the path, you can add one:
export PATH=${PATH}:<your_sdk_dir>/tools.
--------------------------------------------------------------------------
This is how I have set the path:
 export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools
 export PATH
In bashrc.
--------------------------------------------------------------------------
but when I run androi command I get the following error:
lucas05@lucas05-desktop:~/DEVS/android-sdk-linux_86/tools$ android
android: can't find sdkmanager.jar
when I look here /home/lucas05/DEVS/android-sdk-linux_86/tools/lib/sdkmanager.jar the file exist.
>  This is how I have set the path:
 export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools
 export PATH
In bashrc.
export PATH all by itself? that doesn't seem good to me.
try adding this line below your previous line:
```
  export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools/
```
Tell me if that works out!

---

### Post by hoboy on 2010-07-03
> **lkjoel said:**
> export PATH all by itself? that doesn't seem good to me.
try adding this line below your previous line:
```
  export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools/
```
Tell me if that works out!

It didn't help I am getting the same error.
what do you mean by this "export PATH all by itself? "
how should it be done ?

---

### Post by geirha on 2010-07-03
The PATH is set alright, otherwise, running android would've given you a different output. Though, to be sure it's the right android script that gets run, see what this outputs:
```
type android
```
Also, try running the script with -x to see what it tries to do before it fails.

```
sh -x /home/lucas05/DEVS/android-sdk-linux_86/tools/android
```

BTW, exporting the PATH in ~/.bashrc is a bad thing to do. Either put that export line in ~/.profile, or set it in ~/.pam_environment (without export). See [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by lkjoel on 2010-07-03
> **hoboy said:**
> It didn't help I am getting the same error.
what do you mean by this "export PATH all by itself? "
how should it be done ?
export PATH all by itself means this:
```
export PATH
```
That does not make sense at all.

---

### Post by hoboy on 2010-07-04
How can I marked this thread solved ?

---

### Post by Vox754 on 2010-07-04
> **lkjoel said:**
> export PATH all by itself means this:
```
export PATH
```
That does not make sense at all.

You are wrong. The "export" builtin works either with or without assigning something to a variable.

From the bash(1) manual:
```

       export [-fn] [name[=word]] ...
       export -p
              [B]The supplied names are marked for automatic export to the  envi&#8208;
              ronment  of subsequently executed commands.[/B]  If the -f option is
              given, the names refer to functions.  If no names are given,  or
              if  the  -p  option  is  supplied,  a list of all names that are
              exported in this shell is printed.  The  -n  option  causes  the
              export  property  to  be  removed from each name.  [B]If a variable
              name is followed by =word, the value of the variable is  set  to
              word.[/B]   export  returns  an  exit  status of 0 unless an invalid
              option is encountered, one of the names is  not  a  valid  shell
              variable name, or -f is supplied with a name that is not a func&#8208;
              tion.

```

As you can see, the assignment (=word) is optional.


Considering this thread, and [this other one](http://ubuntuforums.org/showthread.php?t=1523629), it seems like you are giving advice that is over your abilities.

---

### Post by lkjoel on 2010-07-04
lol Yeah, that Terminal Enhancements was programmed in 2 minutes, and since it worked, I did even test the security issues, but check my last thread.
And check this one, thats where I got the Idea of Terminal Enhancements:
[http://ubuntuforums.org/showthread.php?t=1513791](http://ubuntuforums.org/showthread.php?t=1513791)

---

### Post by Vox754 on 2010-07-04
> **lkjoel said:**
> lol Yeah, that Terminal Enhancements was programmed in 2 minutes, and since it worked, I did even test the security issues, but check my last thread.
And check this one, thats where I got the Idea of Terminal Enhancements:
[http://ubuntuforums.org/showthread.php?t=1513791](http://ubuntuforums.org/showthread.php?t=1513791)

LOL!

After reading the original thread, [[SOLVED] Random terminal colors](http://ubuntuforums.org/showpost.php?p=9542481&postcount=21), I reiterate: do not follow lkjoel's advice; he most certainly doesn't know enough bash to be trustworthy... and he doesn't have consideration for indentation and white space.

By the way, I love how you took all 2 minutes (you are like the Flash or something!) to implement your new shell, which you ostensibly have called Terminal Enhancements?

---

### Post by lkjoel on 2010-07-05
> **Vox754 said:**
> LOL!

After reading the original thread, [[SOLVED] Random terminal colors]("http://ubuntuforums.org/showpost.php?p=9542481&postcount=21"), I reiterate: do not follow lkjoel's advice; he most certainly doesn't know enough bash to be trustworthy... and he doesn't have consideration for indentation and white space.

By the way, I love how you took all 2 minutes (you are like the Flash or something!) to implement your new shell, which you ostensibly have called Terminal Enhancements?
NO!!
This is a beta version that is just written as a sorta template.
It doesn't work properly!
So that explains the name. The future versions will use the name correctly.
Read the front title again. (it is on my sig)
Ok it was written in 30 secs, asked a few questions, another 30 secs etc...
Yeah, and I am a sorta dirty programmer, but it does take more space and time.
The newer versions will be more readable, but for now, I am just making a template that pretty much only me can understand.
I am using an ASUS EEEPC 700, and I am very, very, very short on disk space!
I am currently not on my 80gig Ubuntu Desktop.

---

### Post by lkjoel on 2010-07-16
Try this and see if it works.
Add these lines to your .bashrc:
```
export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools
export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools/lib
export PATH
```

---

### Post by geirha on 2010-07-16
> **lkjoel said:**
> Try this and see if it works.
Add these lines to your .bashrc:
```
export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools
export PATH=$PATH:/home/lucas05/DEVS/android-sdk-linux_86/tools/lib
export PATH
```

Err, no, don't export anything in .bashrc. That'll prepend those paths several times. Put it in ~/.profile or edit ~/.pam_environment. 

See
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
[http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

And that last line there, «export PATH» is still pointless.

---

### Post by lkjoel on 2010-07-16
> **geirha said:**
> Err, no, don't export anything in .bashrc. That'll prepend those paths several times. Put it in ~/.profile or edit ~/.pam_environment. 

See
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
[http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

And that last line there, «export PATH» is still pointless.
Yes, I was wondering about that export PATH.
But is there any problems with exporting into .bashrc?
On any terminal you load, it will always have that export line right?
Unless you are using tcsh, or sh but usually you would load bash right?
Check the newest version of Terminal Enhancements.
That might help.

---

