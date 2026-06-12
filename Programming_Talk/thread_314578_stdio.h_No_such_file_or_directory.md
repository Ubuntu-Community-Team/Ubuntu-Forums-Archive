---
title: "stdio.h: No such file or directory"
date: 2006-12-07
forum: Programming Talk
---

### Post by prezbedard on 2006-12-07
I just switched my desktop OS to Ubuntu 6.10.

I wanted to play around with C a bit but ran into a problem.

I was getting the error 

```
 stdio.h: No such file or directory
```

I have read through the forums and saw people with the same issue.

I tried 

```
sudo apt-get install build-essential
```

Which gave me an error

I then tried

```
sudo aptitude install build-essential
```

It installed build-essential however it didn't solve the problem I am getting when compiling

my sample program:
```
#include <stdio.h>

int 
main(int argc, char* argv[])
{
    printf ("hello world\n");

    return 0;
}

```

I type

```
gcc test1.c
```

and still get 

```
 stdio.h: No such file or directory

```

What am I doing wrong?

Thanks,

---

### Post by po0f on 2006-12-07
prezbedard,

What's the output of the following commands?
```
[FONT="Courier New"]$ sudo updatedb
$ locate stdio.h[/FONT]
```

---

### Post by foxylad on 2006-12-07
It sounds like either the build-essentials didn't install correctly. Check the contents of /usr/include to see if stdio.h is in there.

---

### Post by prezbedard on 2006-12-08
> **po0f said:**
> prezbedard,

What's the output of the following commands?
```
[FONT="Courier New"]$ sudo updatedb
$ locate stdio.h[/FONT]
```

sudo updatedb

I put the password in , pauses for a few moments then goes back to a prompt no output.

locate stdio.h

produces
```
/usr/lib/perl/5.8.8/CORE/nostdio.h
```

---

### Post by prezbedard on 2006-12-08
> **foxylad said:**
> It sounds like either the build-essentials didn't install correctly. Check the contents of /usr/include to see if stdio.h is in there.

Nope doesn't appear to be there.

---

### Post by bradleyd on 2006-12-08
Code:

sudo apt-get install build-essential

Which gave me an error


what error?

sub #include <stdio.h> with #include <iostream>
you should use iostream instead of outdated stdio.h
["]http://www.cacs.louisiana.edu/~mgr/404/burks/language/cpp/cppfaq/inputout.htm#[15.1]]("http://www.cacs.louisiana.edu/~mgr/404/burks/language/cpp/cppfaq/inputout.htm#[15.1)

---

### Post by prezbedard on 2006-12-08
> **bradleyd said:**
> Code:

sudo apt-get install build-essential

Which gave me an error


what error?

sub #include <stdio.h> with #include <iostream>
you should use iostream instead of outdated stdio.h
["]http://www.cacs.louisiana.edu/~mgr/404/burks/language/cpp/cppfaq/inputout.htm#[15.1]]("http://www.cacs.louisiana.edu/~mgr/404/burks/language/cpp/cppfaq/inputout.htm#[15.1)

```
 sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```

---

### Post by bradleyd on 2006-12-08
> **prezbedard said:**
> ```
 sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```

what do you get when you type apt-cache search build-essential

---

### Post by prezbedard on 2006-12-08
> **bradleyd said:**
> what do you get when you type apt-cache search build-essential


```
 sudo apt-cache search build-essential
sbuild - Tool for building Debian binary packages from Debian sources
```

---

### Post by bradleyd on 2006-12-08
what does your /etc/apt/sources.list look like?

---

### Post by prezbedard on 2006-12-08
> **bradleyd said:**
> what does your /etc/apt/sources.list look like?

```

#deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe


```

---

### Post by Ramses de Norre on 2006-12-08
You'll want to uncomment the two first lines.. Very strange that those are commented..

---

### Post by bradleyd on 2006-12-08
uncomment all of the repositries

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by prezbedard on 2006-12-08
I'll do that. I think I did comment out something in it cause they kept timing out and it was recommended to do so. After I uncomment what is the command I run? is it "apt-get update" ?

Thanks for the help so far.

---

### Post by bradleyd on 2006-12-08
sudo apt-get update && apt-get install build-essential

---

### Post by Ramses de Norre on 2006-12-08
Aptitude is better in general than apt-get.
```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install build-essentials
```

---

### Post by prezbedard on 2006-12-08
It worked!!

Thanks so much.

my next challenge is to get quicken to work so I don't have to boot into windows.

---

### Post by bradleyd on 2006-12-08
your welcome, glad it worked out for you. now just use iostream instead stdio.h and you are ready.Quicken works pretty well with crossover office, just to let you know.
see ya

---

### Post by duff on 2006-12-08
> **bradleyd said:**
> now just use iostream instead stdio.h
NO! He said he's writing C code. iostream is C++ only.

---

### Post by alanhaggai on 2007-08-25
I had the same problem and,
```
sudo apt-get install build-essentials
```

worked out well! :guitar:

---

### Post by scopsey on 2007-08-26
I'm suffering the same issue but having tried all the above I still get 'stdio.h: No such file or directory'

When running the suggested commends I keep getting 'Couldn't find package build-essentials' which I'm guessing may be related!

BTW My install was done using the latest 32bit Ubuntu 7.04 build from the download live/install ISO

Everything else works brilliantly - Hazzar!

Any further suggestions welcomed.

---

### Post by fct on 2007-08-27
> **scopsey said:**
> When running the suggested commends I keep getting 'Couldn't find package build-essentials' which I'm guessing may be related!

Try with build-essential (note the final s is gone) instead.

---

### Post by jap1968 on 2007-08-28
The package that you need to install in order to include the C standard libraries is **libc6-dev**

---

### Post by scopsey on 2007-08-31
> **fct said:**
> Try with build-essential (note the final s is gone) instead.

Excellent! That worked :-) 

Thank you loads!

Simon

---

### Post by kichimi on 2007-09-01
hey, i have the same problem, ive tried all the steps and this is the output to them.

```
root@quantum:/home/kichimi/programming# cc echo.c
echo.c:1:20: error:  stdio.h: No such file or directory
echo.c: In function âmainâ:
echo.c:5: warning: incompatible implicit declaration of built-in function âprintfâ
echo.c:6: error: expected â;â before â}â token
echo.c:4: warning: return type of âmainâ is not âintâ
root@quantum:/home/kichimi/programming#

```

So i tried using locate to find it.

```

root@quantum:/home/kichimi/programming# updatedb
root@quantum:/home/kichimi/programming# locate stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h
/usr/include/bits/stdio.h
/usr/include/stdio.h
root@quantum:/home/kichimi/programming#

```

Then i tried to compile with both C + GCC compilers

```

root@quantum:/home/kichimi/programming# gcc echo.c
echo.c:1:20: error:  stdio.h: No such file or directory
echo.c: In function âmainâ:
echo.c:5: warning: incompatible implicit declaration of built-in function âprintfâ
echo.c:6: error: expected â;â before â}â token
echo.c:4: warning: return type of âmainâ is not âintâ
root@quantum:/home/kichimi/programming# cc echo.c
echo.c:1:20: error:  stdio.h: No such file or directory
echo.c: In function âmainâ:
echo.c:5: warning: incompatible implicit declaration of built-in function âprintfâ
echo.c:6: error: expected â;â before â}â token
echo.c:4: warning: return type of âmainâ is not âintâ
root@quantum:/home/kichimi/programming#

```

What am i doing wrong??


Actually, Scrap that, i found out the problem! I am a idiot ;) It was a code error..Silly me. Sorry

---

### Post by paul94 on 2007-09-02
I have the same issue but having tried all the suggestions I still get 'error: stdio.h: No such file or directory'. I am using ubuntu 7.04 - the Feisty Fawn. Any more help

---

### Post by DMills on 2007-09-02
"stdio.h" Vs <stdio.h> possibly?

System headers are included as <stdio.h>, not "stdio.h" which would imply searching the local directory rather then the system include path.

It would help to have a look at your test program.

---

### Post by paul94 on 2007-09-02
Thanks for the very quick response. I am using a simple c program for testing. 

#include <stdio.h>



int main()

{

  int i;

  for(i=5;i<=1000;i+=5) printf("%d\t" , i);

  return(0);

}

Output from 'gcc 1000.c -o 1000
1000.c:1:19: error: stdio.h: No such file or directory
1000.c: In function ‘main’:
1000.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

Hope this is helpful.

---

### Post by fct on 2007-09-03
Compiles perfectly on my system. There is something wrong with your setup.

Try "sudo apt-get install --reinstall build-essential".

---

### Post by paul94 on 2007-09-03
I have tried your solution but do not seem to have 'build-essential'. Here is the result...
paul@paul-laptop:~$ sudo apt-get install --reinstall build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
paul@paul-laptop:~$ 

Thank you

---

### Post by fct on 2007-09-03
You might have a problem with your repositories. Try "sudo apt-get update" and then try to install again.

Failing that you need to check your repository list in /etc/apt/sources.list . This entry might be helpful:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by paul94 on 2007-09-03
:) Thank you very much. I needed to follow your suggestion to go  to the Repositories and update. I noticed that one of the packages was the lib for c. Having run install and gcc all is now well. Thank you once again.
paul :)

---

### Post by kredei on 2007-09-08
I'm also getting an error when trying to compile anything. I checked my packages and libc6-dev isn't installed. When trying to install it, I get the following error;

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.6.1-1+b1 is to be installed

The solution that aptitude proposes seems a little intense:

Remove the following packages:
kmymoney2
libavcodec1d
libavutil1d
libdb4.6
libgpod2
liblzo2-2
libopencdk10
libpostproc1d
libxine-extracodecs
libxine1-ffmpeg
nethack

Downgrade the following packages:
gstreamer0.10-x [0.10.14-2 (now) -> 0.10.12-0ubuntu1 (feisty)]
libc6 [2.6.1-1+b1 (now) -> 2.5-0ubuntu14 (feisty)]
libc6-i686 [2.6.1-1+b1 (now) -> 2.5-0ubuntu14 (feisty)]
libdbus-1-3 [1.1.1-3 (now) -> 1.0.2-1ubuntu4 (feisty-updates)]
libdbus-glib-1-2 [0.74-1 (now) -> 0.73-1 (feisty)]
libfreetype6 [2.3.5-1+b1 (now) -> 2.2.1-5ubuntu1 (feisty)]
libglade2-0 [1:2.6.2-1 (now) -> 1:2.6.0-3 (feisty)]
libgnutls13 [1.7.18-2 (now) -> 1.4.4-3build1 (feisty)]
libgstreamer-plugins-base0.10-0 [0.10.14-2 (now) -> 0.10.12-0ubuntu1 (feisty)]
libgstreamer0.10-0 [0.10.14-1 (now) -> 0.10.12-0ubuntu2 (feisty)]
libgtk2.0-0 [2.10.13-1 (now) -> 2.10.11-0ubuntu3 (feisty)]
libhal1 [0.5.9.1-4 (now) -> 0.5.9-1ubuntu2~feisty1 (feisty-backports)]
libncursesw5 [5.6+20070812-1 (now) -> 5.5-5ubuntu2 (feisty)]
libpango1.0-0 [1.16.5-1 (now) -> 1.16.2-0ubuntu1 (feisty)]
libssl0.9.8 [0.9.8e-6 (now) -> 0.9.8c-4build1 (feisty)]
libvorbis0a [1.2.0.dfsg-2 (now) -> 1.1.2.dfsg-1.2ubuntu2 (feisty-security)]
libxine1 [1.1.7-3 (now) -> 1.1.4-2ubuntu3 (feisty)]
libxml2 [2.6.30.dfsg-1 (now) -> 2.6.27.dfsg-1ubuntu3 (feisty)]
python2.4 [2.4.4-6 (now) -> 2.4.4-2ubuntu7 (feisty)]
python2.4-minimal [2.4.4-6 (now) -> 2.4.4-2ubuntu7 (feisty)]
rhythmbox [0.10.1-1+b1 (now) -> 0.10.0-0ubuntu2 (feisty)]
zlib1g [1:1.2.3.3.dfsg-5 (now) -> 1:1.2.3-13ubuntu4 (feisty)]

Leave the following dependencies unresolved:
libxine1 recommends libxine1-ffmpeg
Score is -5989

Does anyone know a better way to fix this?

---

### Post by dwhitney67 on 2007-09-08
Hint????
> This may mean that the package is missing, ...

Run:

$ sudo apt-get install build-essential

---

### Post by fct on 2007-09-09
kredei, to me it looks like you're using repositories that are not official and may be messing up the install. One of those may have a new libc6 version without the accompanying libc6-dev.

---

### Post by beruic on 2007-09-10
I had the same problem.
After installing build-essentials, i checked again with
```
sudo updatede
locate stdio.h
```
it found
```
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h
```
but the compiler still gave the message.
I checked the folder and found the a.out had been compiled (and worked, and a file named ' (yes, only that... i think) was there. Well... now the are gone, and now it works :)

---

### Post by kredei on 2007-09-15
fct -- thanks, you were right, everything works now!

---

### Post by beruic on 2007-09-18
Am I the only one who thought that Windows had a monopoly on strange solutions? :D

---

### Post by arijarot on 2007-11-18
I have followed all that was suggested above. Build essential is installed correctly. But I still get the following error message: ```
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:4: warning: return type of ‘main’ is not ‘int’

```

This is the file hello.c

```
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}

```

---

### Post by geirha on 2007-11-18
```

#include < stdio.h>
          ^
remove that space.

```

---

### Post by arijarot on 2007-11-18
That worked! Thanks, geirha. 

So, this site, from which I got the code, has mistakes in it? [http://www.physics.drexel.edu/courses/CompPhys/General/C_basics/c_tutorial.html](http://www.physics.drexel.edu/courses/CompPhys/General/C_basics/c_tutorial.html)

p.s., still get the following errors ```
hello.c: In function ‘main’:
hello.c:4: warning: return type of ‘main’ is not ‘int’

```.

---

### Post by geirha on 2007-11-18
the proper POSIX way is to have main return 0 on succes, and any other int on failure, so do something like ```
int main()
{
    // some code ...
    if (something_went_wrong())
        return 1;
    return 0;
}
```

---

### Post by arijarot on 2007-11-18
> **geirha said:**
> the proper POSIX way is to have main return 0 on succes, and any other int on failure, so do something like ```
int main()
{
    // some code ...
    if (something_went_wrong())
        return 1;
    return 0;
}
```

OK. I'll give that a try. Thanks again :)

---

### Post by Free Hugs on 2008-01-09
FYI - I had trouble getting GCC to work correctly (stdio.h missing) and found this thread. 

It was working on my laptop (Ubuntu 7.10 with gnome and kde) but it wasn't working on my desktop (Xubuntu 7.10). I did ```
sudo apt-get install build-essential
```
and that worked perfectly!
I figured it dragged all the necessary libraries and header files for the compiler over with the install of Kdevelop, but that appears to have been my mistake...

---

### Post by LaRoza on 2008-01-10
> **Free Hugs said:**
> FYI - I had trouble getting GCC to work correctly (stdio.h missing) and found this thread. 

It was working on my laptop (Ubuntu 7.10 with gnome and kde) but it wasn't working on my desktop (Xubuntu 7.10). I did ```
sudo apt-get install build-essential
```
and that worked perfectly!
I figured it dragged all the necessary libraries and header files for the compiler over with the install of Kdevelop, but that appears to have been my mistake...

Yes, that is old news. The stickies address it.

---

### Post by harishankar on 2008-01-26
I too have the same problem..but i tried

sudo apt-get install build-essential

all components were installed..and moreover when looking at Synaptic packet manager i could see **libc6-dev** been installed..inspite of all these when i searched for stdio.h i got

hash-desktop:~$ locate stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h
hash-desktop:~$ 

but when i looked in the directory **/usr/include** i could see stdio.h file is there..when i tired compiling a simple c program i couldnt do it...wat i have to do now??

---

### Post by LaRoza on 2008-01-26
> **harishankar said:**
> I too have the same problem..but i tried

sudo apt-get install build-essential

all components were installed..and moreover when looking at Synaptic packet manager i could see **libc6-dev** been installed..inspite of all these when i searched for stdio.h i got

hash-desktop:~$ locate stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h
hash-desktop:~$ 

but when i looked in the directory **/usr/include** i could see stdio.h file is there..when i tired compiling a simple c program i couldnt do it...wat i have to do now??

What did you try to do? Did you try: [http://ubuntuprogramming.wikidot.com/C](http://ubuntuprogramming.wikidot.com/C)

Follow that, and post any errors you get.

---

### Post by geirha on 2008-01-26
> **harishankar said:**
> 
hash-desktop:~$ locate stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h
hash-desktop:~$

Just a note on this. The locate command doesn't search through your filesystems (harddrives), it searches through a database. That database is updated once a day (by default) with the location of all files on your mounted filesystems, so locate is not the command to use for searching for files that were added less than a day ago.

---

### Post by Jessehk on 2008-01-26
> **kichimi said:**
> hey, i have the same problem, ive tried all the steps and this is the output to them.
<SNIP>


Why are you compiling software as root? Logging in as root to do anything other than system administration is extremely dangerous.

---

### Post by harishankar on 2008-01-27
I tried to install pidgin...at the time of config and make file i get a error stating..**C compiler cannot create executables** wat is the problem??

---

### Post by WonRyong on 2008-05-28
I installed ubuntu 8.04 LTS two days ago.

Same error occurs.

I solve this problem as following:


sample1.c

```
#include <stdio.h>

int 
main(int argc, char* argv[])
{
    printf ("hello world\n");

    return 0;
}

```


wonryong@wonryong-desktop:~/c$ gcc sample1.c
sample1.c:1:19: &#50724;&#47448;: stdio.h: No such file or directory
sample1.c: In function ‘main’:
sample1.c:6: warning: incompatible implicit declaration of built-in function ‘printf’
wonryong@wonryong-desktop:~/c$ sudo apt-get update && sudo apt-get install build-essential
...
wonryong@wonryong-desktop:~/c$ gcc sample1.c
wonryong@wonryong-desktop:~/c$ ./a.out
hello world
wonryong@wonryong-desktop:~/c$

---

### Post by inportb on 2008-05-28
Yep. build-essential is the shiz. It's not installed by default because not everyone needs to build stuff.

---

### Post by LaRoza on 2008-05-28
Yeah, the subject of this thread, and the information the sticky has ;)

---

### Post by shankhs on 2008-05-28
hey i kinda installed g++ using software sources there i went to origun->not  installed and checked g++ (mark for installation) then it prompted for cd ani i did not have cd for 7.10 so i cancelled it now wen i am tryin to reinstall it its lost!!!! itz not there its not in the installed area but obsolete packages..
what should i do?

---

### Post by LaRoza on 2008-05-29
> **shankhs said:**
> hey i kinda installed g++ using software sources there i went to origun->not  installed and checked g++ (mark for installation) then it prompted for cd ani i did not have cd for 7.10 so i cancelled it now wen i am tryin to reinstall it its lost!!!! itz not there its not in the installed area but obsolete packages..
what should i do?

Go to System->Administration->Software Sources and uncheck the CD.

Run this after:

```

sudo apt-get update && sudo aptitude install build-essential

```

---

### Post by shankhs on 2008-05-29
hey thanx

---

### Post by madhanacdc on 2008-07-10
> **WonRyong said:**
> I installed ubuntu 8.04 LTS two days ago.

Same error occurs.

I solve this problem as following:


sample1.c

```
#include <stdio.h>

int 
main(int argc, char* argv[])
{
    printf ("hello world\n");

    return 0;
}

```


wonryong@wonryong-desktop:~/c$ gcc sample1.c
sample1.c:1:19: &#50724;&#47448;: stdio.h: No such file or directory
sample1.c: In function ‘main’:
sample1.c:6: warning: incompatible implicit declaration of built-in function ‘printf’
wonryong@wonryong-desktop:~/c$ sudo apt-get update && sudo apt-get install build-essential
...
wonryong@wonryong-desktop:~/c$ gcc sample1.c
wonryong@wonryong-desktop:~/c$ ./a.out
hello world
wonryong@wonryong-desktop:~/c$

thanks man... this one worked perfectly

---

### Post by Ichimonji10 on 2008-12-27
> **LaRoza said:**
> Go to System->Administration->Software Sources and uncheck the CD.

Run this after:

```

sudo apt-get update && sudo aptitude install build-essential

```

These two steps worked perfectly for me. Thanks.

---

### Post by Felguild on 2009-02-11
I tried 

> sudo apt-get install build-essential

but gave me this

> WARNING: The following packages cannot be authenticated!
  libc6-dev libstdc++6-4.1-dev g++-4.1 g++ dpkg-dev build-essential
Install these packages without verification [y/N]? 

Followed by a lot of Errors like

> Err [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4
  404 Not Found [IP: 91.189.88.31 80]


any help?
Thanks

---

### Post by geirha on 2009-02-11
Support for feisty ended october 2008. Seems the repositories might have been removed.

---

### Post by absk on 2009-03-06
> **fct said:**
> Try with build-essential (note the final s is gone) instead.
thanks.. removing the 's' worked.

---

### Post by anu m m on 2009-03-25
Hi,
  
I had the same problem "stdio.h :No such file or directory problem"

I uncommented some lines /etc/apt/sources.txt as mentioned in previous threads, and now dont get the above error.

But when i give gcc <filename.c> 

I get this message
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit statusI get following message as well

I installed ubuntu 8.04 LTS

---

### Post by anu m m on 2009-03-25
One more thinh when i tried 
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install build-essentials

it gave following errors too
Couldn't find any package whose name or description matched "build-essentials"
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
  407 Proxy Authentication Required

Please suggest wat is wrong

---

### Post by anu m m on 2009-03-25
hey,

I got a link with the same issue,
[http://ubuntuforums.org/showthread.php?t=190193](http://ubuntuforums.org/showthread.php?t=190193)

I installed the libc6-dev

And now am able to compile and run a simple c code

Thanks:)

---

### Post by geirha on 2009-03-25
> **anu m m said:**
> sudo aptitude update && sudo aptitude upgrade && sudo aptitude install build-essentials

For future reference, it's [build-essential](apt:build-essential) (without the plural s)

---

### Post by cmwarre on 2009-09-30
Hey Guys I'm getting the same problem.  Except when I typed sudo apt-get update it prompted me for my password.  Then it tole me the command sudo can't be found...  I'm not sure why sudo would ask me for my password then disappear...  

The latest thing that I have done through the terminal is install lynx.  Other than that I have been able to compile and run ALL of my c programs until just now...

---

### Post by bradleyd on 2009-10-01
type dpkg -l | grep sudo

and paste back the results

---

### Post by cmwarre on 2009-10-02
-bash: dpkg: command not found

---

### Post by Reiger on 2009-10-02
Means you do not have a deb package installer; or at least you cannot access it from bash.

---

### Post by Can+~ on 2009-10-02
I'm guessing that you're running a non-debian distribution (RPM maybe?).

---

### Post by bradleyd on 2009-10-02
I am assuming you are on a deb based distro being that you installed lynx and ran apt-get update.  Maybe your path jacked up, try this:
echo $PATH

report back the results. Also what does your .bashrc file look like?

---

### Post by spijoe1 on 2009-12-03
Hello, I am currently working on a project which requires the use of an open source environment. I have to install a 76CS1 card.  I have never installed anything on linux before, but I have the instructions I should follow. I tried them out but I got this error : stdio.h: No such file or directory , when tried to compile using :make.

Can anybody know what might be the problem, I have tried :sudo aptitude install build-essential
but it still give me the same error.

---

### Post by Arndt on 2009-12-03
> **spijoe1 said:**
> Hello, I am currently working on a project which requires the use of an open source environment. I have to install a 76CS1 card.  I have never installed anything on linux before, but I have the instructions I should follow. I tried them out but I got this error : stdio.h: No such file or directory , when tried to compile using :make.

Can anybody know what might be the problem, I have tried :sudo aptitude install build-essential
but it still give me the same error.

How far did you get when doing the things recommended at the beginning of this thread?

---

### Post by spijoe1 on 2009-12-03
I cd to my driver source and then i typed : make testn (where n was just any number between 1 and 6)

---

### Post by Arndt on 2009-12-03
> **spijoe1 said:**
> I cd to my driver source and then i typed : make testn (where n was just any number between 1 and 6)

Do you mean to say you tried none of the things suggested in the thread?

---

