---
title: "PHP,fopen, and large files (&gt;2gig)"
date: 2007-10-22
forum: Programming Talk
---

### Post by lavajumper on 2007-10-22
I've been working on some PHP scripts to parse some largeish data files which make extensive use of fopen, fseek, ftell, fgets and fputs. It craps out on any file over 2.? gigs. 

From my searches, it seems I need to recompile PHP with a switch for 64 bit ints. We're running the scripts on a 6.06LTS box, and the prospect of compiling PHP and breaking future updates , etc. isn't too appealing.

  Does anyone know a way to get PHP working on large files without recompiling? Like, a PHP package in synaptic?

---

### Post by #Reistlehr- on 2007-10-22
Well just so you understand, when you read/open a file with PHP, it opens it to RAM. So you need to make sure you have enough ram for it. A few things to try are:

ini_set(&#8221;memory_limit&#8221;,&#8221;16M&#8221;);
Where 16M is whatever you want it to be. The larger the better, but it will become a system hog, and anyhting over 128 is not recommended. You can add this line before any header or session functions near the top of the script so it gets executed first. Make sure to read up on the documentation though.

Also, instead for fread, fseek, try

file_get_contents('File To Parse'); The nice thing about file_get_contents() is you can open a local or remote file.

Just a question, why are you wanting to open files that large?

---

### Post by archivator on 2007-10-22
> **#Reistlehr- said:**
> Well just so you understand, when you read/open a file with PHP, it opens it to RAM. So you need to make sure you have enough ram for it. A few things to try are:

ini_set(”memory_limit”,”16M”);
Where 16M is whatever you want it to be. The larger the better, but it will become a system hog, and anyhting over 128 is not recommended. You can add this line before any header or session functions near the top of the script so it gets executed first. Make sure to read up on the documentation though.

Also, instead for fread, fseek, try

file_get_contents('File To Parse'); The nice thing about file_get_contents() is you can open a local or remote file.

Just a question, why are you wanting to open files that large?
Wow! You're wrong on numerous levels!

First, opening a file descriptor does not copy the contents of the file in memory. Never! Thus, changing the memory limit will change nothing.

Second, why would anyone try to copy a 2GB in memory?! Once you answer that question, you'll see that file_get_contents is absolutely unneeded and in fact is the worst possible solution. 

As to the problem at hand, I am yet to see a PHP version for Ubuntu with LFS. Sorry to disappoint you. 

Post Scriptum: Reistlehr-, no harsh feelings. It's just that your post is extremely misleading.

---

### Post by #Reistlehr- on 2007-10-22
> **archivator said:**
> Wow! You're wrong on numerous levels!

First, opening a file descriptor does not copy the contents of the file in memory. Never! Thus, changing the memory limit will change nothing.

You are actually wrong on this. Perhaps you mis-understood what i was saying, but any string that is running in a script is in RAM, until the script has gracefully exited. Use this example i wrote up to help clear things up:
```

<?php
echo "---- This Is Using FOPEN() and FREAD() ----<br />";
echo 'At this point, '. memory_get_usage().' bytes  of RAM is being used.<br>';

$fOpen = fopen(__FILE__, "r");
$FileContents = fread($fOpen, filesize(__FILE__) );

echo 'At this point, '. memory_get_usage().' bytes  of RAM is being used.<br>';

fclose($fOpen);
unset($FileContents);
echo 'At this point, '. memory_get_usage().' bytes  of RAM is being used.<br>';

echo "<br />---- This Is Using FILE_GET_CONTENTS() ----<br />";
echo 'At this point, '. memory_get_usage().' bytes  of RAM is being used.<br>';

$FileContents = file_get_contents(__FILE__);

echo 'At this point, '. memory_get_usage().' bytes  of RAM is being used.<br>';

unset($FileContents);
echo 'At this point, '. memory_get_usage().' bytes  of RAM is being used.<br>';
?> 

```

As you can see, it will load itself using fread first, and it states the memory usage before, during, and after. It is followed by a clone but with file_get_contents.

> **archivator said:**
> Second, why would anyone try to copy a 2GB in memory?! Once you answer that question, you'll see that file_get_contents is absolutely unneeded and in fact is the worst possible solution.
This there is no comment as i would not recommend opening files that large in the first place. 

> **archivator said:**
> 
As to the problem at hand, I am yet to see a PHP version for Ubuntu with LFS. Sorry to disappoint you. 
There are a few ways to get large file support if you custom compile, but sadly as you have stated, Ubuntu does not supply any kind of this in the repo's

> **archivator said:**
> Post Scriptum: Reistlehr-, no harsh feelings. It's just that your post is extremely misleading.

I don't want to sound rude either, but  I think perhaps you jumped too quickly to answer. If you can prove me wrong, then of course i am wrong, and i'll admit to it, plus it's a great learning experience.



Also lava, this might be something to check into if it is 100% neccessary:
[quote=PHP Documentation]
I thought I had an issue where fread() would fail on files > 30M in size. I tried a file_get_contents() method with the same results. The issue was not reading the file, but echoing its data back to the browser.

Basically, you need to split up the filedata into manageable chunks before firing it off to the browser:

<?php

$total     = filesize($filepath);
$blocksize = (2 << 20); //2M chunks
$sent      = 0;
$handle    = fopen($filepath, "r");

// Push headers that tell what kind of file is coming down the pike
header('Content-type: '.$content_type);
header('Content-Disposition: attachment; filename='.$filename);
header('Content-length: '.$filesize * 1024);
               
// Now we need to loop through the file and echo out chunks of file data
// Dumping the whole file fails at > 30M!
while($sent < $total){
    echo fread($handle, $blocksize);
    $sent += $blocksize;
}
           
exit(0);

?>

Hope this helps someone!
[/quote]
[http://us.php.net/fread](http://us.php.net/fread)

---

### Post by lavajumper on 2007-10-23
Kudos to both of you, and thank you for the information.

Just a couple of things that might clear the air. We're parsing large data files, some of them up to 20 gigs, for database purposes. 

The "extensive" use of fgets, ftell, and fseek are how we "manage" RAM usage, which I believe Archivator picked up on. (Thanks for the info on LFS) 

When you call fopen, nothing of the file is read into memory, it only creates a descriptor of the file you want to work on. Included in this descriptor is a pointer to a position in the file which is an integer type, and must be able to point to any byte in the file. So if the file has more bytes than the integer can address, fopen fails because it cannot address the entire file. (Read a little about what happens when you add 1 to an int that's maxed out)  In the Ubuntu (and most other) distribution, that integer type goes up to 2^31 (32-1) which tops at 2147483648 bytes.

I know these files have "\n" as a record deliminator, so I can control how much RAM is used by calling fgets n times, and only working on a "chunk" of the file at any given time. Using ftell and fseek you can save the file positon and move about the file at will without dragging the whole thing into RAM. This gives me the ability to work on a 4 gig file and only use 20K of RAM (or whatever I wish).  

#Reistlehr is right that: 
```

$fOpen = fopen(__FILE__, "r");
$FileContents = fread($fOpen, filesize(__FILE__) );

```

will copy '__FILE__'  into RAM because he tells fopen to read 'filesize' bytes, but the fread function can grant much more control if you track the file position and fread n bytes, at the cost of the developer handling file position, EOF, and other file conditions. 

And for the problem at hand, I pulled down the php source and built a n LFS version of php off to the side. After looking over the scripts, I found they don't do anything the base installation doesn't provide. If anyone is interested the command is:
```

prompt# CFLAGS="-D_FILE_OFFSET_BITS=64" ./configure

```
to configure the build. I also had to add in the libxml2-dev package.

---

### Post by archivator on 2007-10-23
As lavajumper pointed out, when using a well-designed file format, there is no need to read an entire file into the memory. 

For example, if the format is specified as ```
<db size>\n
<record size><record>\n
```, one can easily read the first record without needing to parse the entire database. In this scenario, the record is of variable size, so it is impossible to jump straight to the n-th record. To do that, one would need to read the previous records' length and fseek past it.

My point being that reading a flat-file database in memory is in most cases a suicide attempt. If it doesn't crash when you test it, it *will* crash when you reach a large enough amount of records.

---

### Post by lavajumper on 2007-10-23
Just for correctness
> 
he tells fopen to read 'filesize' bytes

should be:
> he tells fread to to read 'filesize' bytes....kind of critical in this thread. ;)

---

### Post by #Reistlehr- on 2007-10-23
lol. Very very true.

Did you compile the your second instance of php with Apache support or no?

Just wondering.

---

### Post by lavajumper on 2007-10-23
PHP constantly impresses me and I've started using it in place of PERL and BASH for our "quick and dirty's"; PHP! Its not just for the web anymore! 

So...
No apache.  These are backend processors that are fired off the command line either manually or by cron, so they're never touched by any of the web servers.

The default "make install" conveniently dropped the new installation entirely in "/usr/local/<whatever>" so there was no contamination, which means the new build won't get fubar'd by Ubuntu updates, and production code remains running on the 'standard' Ubuntu installs(with all the toys).

---

### Post by #Reistlehr- on 2007-10-23
Yeah, thats what i wanted to check.

Personally, i don't use PHP for JUST the web either. I made a script to manage my iPod (still have a problem reading the DB, but for the most part it works), made a script to manage my documents, and texts. Got sciprts that sync my 2 servers and my mythbox.. i love it! A lot of people have the mindset it's JUST for the web, which is sad. They don't see the potential.

---

### Post by lavajumper on 2007-10-27
Just in case anyone is watching this thread, the complie switch above only provided limiited functionality. ftell and fseek still do not work. fopen will open the file and fgets appears to work if you just start at the beginning of the file and go through without moving the file pointer yourself.

<sigh>

---

### Post by bunker on 2007-10-27
If you're still having a problem, perhaps you might have greater  success using C -- or some other language that has a low-level to the i/o functions -- to split the file up into more managable chunks for your processing script.

All you need is to open the file using 
```
int fd = open(path, O_RDONLY|O_LARGEFILE);
```
and make sure all your offsets are of type _off64_t_ (in sys/types.h).  Then use read(2) and write(2) and creat(2) to copy the file into chunkable parts.

By the way, there a php compile switch to enable posix-like functions (--enable-posix).  I have never actually used them, but maybe they will give you the same interfaces?  If memory serves, they are enabled by default.

---

### Post by pmasiar on 2007-10-29
To stay with more flexible languages than low-level C, is using Python an option?

---

### Post by lavajumper on 2007-11-01
We're splitting the files into 1.8 gig chunks using C. (good suggestion, thanks)

We actually do most of the heavy lifting on these files with C processes, and php takes care of a "stage 2.5" process which, really _should_ be done in C.  We wrote these in php because it was quicker to write out and test,  and the perfomance cost was acceptable.  Its nice to have php handle some of the array gymnastics. 

As far as python goes, the only strike is that no one here has written in it, so we'd be climbing the curve. But.. this might be the time start.

---

### Post by bunker on 2007-11-01
You have to compile python specifically to handle large files in the same way as PHP.  I can't find the docs for this, but I remember it said "this might work" so I read that as "use another language" ;).

As for learning python, if you write good PHP you'll find it pretty easy.  I think [subjectively] that it is less flexible than php under some cases.  It seems to me that either I can write a bash script type program or some huge project, but for things a in between I found myself to be fighting the language all the time (sometime *I* know the problem better than the compiler ^^), and the documentation is terrible.  I [subjectively] prefer ruby to python after giving both a good go, but meh, maybe I was just using it wrong ;).

---

### Post by LaRoza on 2007-11-01
> **bunker said:**
> You have to compile python specifically to handle large files in the same way as PHP.  I can't find the docs for this, but I remember it said "this might work" so I read that as "use another language" ;).

As for learning python, if you write good PHP you'll find it pretty easy.  I think [subjectively] that it is less flexible than php under some cases.  It seems to me that either I can write a bash script type program or some huge project, but for things a in between I found myself to be fighting the language all the time (sometime *I* know the problem better than the compiler ^^), and the documentation is terrible.  I [subjectively] prefer ruby to python after giving both a good go, but meh, maybe I was just using it wrong ;).

Perhaps you better give Python another go. The documentation is the best of any language I have seen, and I have never fought the language.

I will give Ruby another chance also :-)

---

### Post by fullout-blaine on 2008-07-23
I just spent three days figuring out how to have my server download large files (size > 30MB) from outside the web root to the client via their web browser with PHP.  I finally got it to work and I wanted to share my solution in case someone else is having the same problem.

**The problem:** file downloads stop at around 30MB without warning.

**My failed solution:** 
-set_time_limit(big number)
-use fopen and fread to send the file in chunks as proposed in this thread and [http://php.net/manual/en/function.readfile.php](http://php.net/manual/en/function.readfile.php) 

**The key to solving the problem:**
The server was timing out and failing silently.  My download script is installed on IIS 6 (PHP installed as a CGI).  IIS 6 sets the default timeout for CGI applications at 300 seconds.  So despite, the value of max_execution_time in the php.ini and the value passed to php by set_time_limit, all php scripts in this server configuration are also constrained by the CGI timeout value (300 seconds by default).  

**_To correct the problem you must increase the CGI timeout in IIS._**  In IIS 6 you must edit the metabase to change the timeout.  The following link describes the procedure nicely: [http://www.iisadmin.co.uk/?p=7](http://www.iisadmin.co.uk/?p=7)

I hope this helps.

---

