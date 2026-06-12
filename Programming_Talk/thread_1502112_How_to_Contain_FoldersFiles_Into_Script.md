---
title: "How to Contain Folders/Files Into Script?"
date: 2010-06-05
forum: Programming Talk
---

### Post by huangyingw on 2010-06-05
Hello,
	I am requested by boss to write such a script:
	1:It will install(in my understand, copy) PHP codes in a certain director, like /var/www/html/MY-PHPX_Y_Z
	2:The shell script should include the PHP codes in it. My understanding is that the folders/files should be embeded in my shell, for example "install.sh"
	My question is: could the shell itself contains folders and files in it? And if yes, how could I extract them out exactly from my shell?
	I have googled this question, and I only got this URL:[http://mspo.com/embedfilesinshell.html](http://mspo.com/embedfilesinshell.html)
	But, I failed at this step:```
uuencode myApp.tar.gz myApp.tar.gz >> myApp_install.sh
``` I have installed uuencode in my Ubuntu 10.4, 
	but the above command just hang. I don't knwo why.

---

### Post by lostinxlation on 2010-06-05
uuencode is a command to generate ASCII characters out of binary. Is that what you want ?

---

### Post by prshah on 2010-06-05
> **huangyingw said:**
> I failed at this step:```
uuencode myApp.tar.gz myApp.tar.gz >> myApp_install.sh
``` I have installed uuencode in my Ubuntu 10.4

> **lostinxlation said:**
> uuencode is a command to generate ASCII characters out of binary.

Actually, uuencode is needed here so that the binary file can be converted to ASCII characters and "attached" to the shell script.

Note that if your (binary) file is large, the uuencode command can seem to "hang", but you should notice some CPU/Disk activity.

Alternately, you can run the command without the ">>..." part of it and see what you get on the screen (You should get a bunch of weird ASCII characters). If you get a request prompt of any sort, post back for tips on how to go around this.

The tutorial you are following is exactly right for what you want to do.

---

### Post by huangyingw on 2010-06-06
> **prshah said:**
> Actually, uuencode is needed here so that the binary file can be converted to ASCII characters and "attached" to the shell script.

Note that if your (binary) file is large, the uuencode command can seem to "hang", but you should notice some CPU/Disk activity.

Alternately, you can run the command without the ">>..." part of it and see what you get on the screen (You should get a bunch of weird ASCII characters). If you get a request prompt of any sort, post back for tips on how to go around this.

The tutorial you are following is exactly right for what you want to do.
Yes, thanks for your detail explanation&#65292; I have successfully tried the uuencode command, I&#12288;will next try the uudecode command.

---

### Post by huangyingw on 2010-06-07
Hello,
    A bad news:the target machine I intended to run this script has not installed "uudecode" and "uuencode". And I am also not sure that othner machines have them installed.
    So, how could I realize my goal without "uuencode" & "uudecode" commands?

---

### Post by lostinxlation on 2010-06-07
I don't know about PHP , but can't you just have a separate binary file(tar.gz) which is downloadable ?
If you want to include the binary archives in a file, uuencode/uudecode is the only way, as far as I know.. That's how email/usenet could accommodate the binary data in it long long long time ago.

---

### Post by prshah on 2010-06-07
> **huangyingw said:**
> the target machine I intended to run this script has not installed "uudecode" and "uuencode".

Unfortunately, there is no way to "attach" a binary file to a script without converting it to ASCII text. To convert, you need to use uuencode and uudecode. 

If you cannot access the programs, you can write your own uuencode/uudecode scripts. I've never done it, but I think it should be relatively easy. Use the [source code]("http://people.sc.fsu.edu/~burkardt/c_src/uuencode/uuencode.html") for hints.

You can also take a look at [makeself]("http://megastep.org/makeself/") which seems to have a custom way to integrate binary files into a shell script.

---

### Post by nvteighen on 2010-06-07
Wait a bit... the whole thing is a design failure.

PHP files aren't binary files... So, you can "embed" them by creating a string variable with their content in your SH script and also record in another variable where each PHP file should be created. Does SH/Bash support dictionaries? If not, use Perl: a dict structure would be handy here to relate the PHP source with its path.

Then, make the script check whether the path exists, if not, create it and then copy the contents into the file. What I want you to see is that you don't need the copy the whole file structure in order to construct it. Let mkdir do that... just record how it looked like.

Of course, the drawback is that you won't be able to reuse the code for different files. To make it reusable, you'd have to take a metaprogramming approach, such that you create a script that generates a new shell script with the sources of whatever you want to be installed wherever you like.

IMO, the whole thing is totally absurd, as a .tar.gz with a Makefile would be enough, but well, your boss is your boss. Moreover, the whole thing seems like poorly reinventing a .deb-like "installer"... Maybe a .deb could be a solution if it happens to be a Debian-like OS (or a .rpm, if it's Red Hat-based).

---

### Post by huangyingw on 2010-06-07
> **nvteighen said:**
> Wait a bit... the whole thing is a design failure.

PHP files aren't binary files... So, you can "embed" them by creating a string variable with their content in your SH script and also record in another variable where each PHP file should be created. Does SH/Bash support dictionaries? If not, use Perl: a dict structure would be handy here to relate the PHP source with its path.

Then, make the script check whether the path exists, if not, create it and then copy the contents into the file. What I want you to see is that you don't need the copy the whole file structure in order to construct it. Let mkdir do that... just record how it looked like.

Of course, the drawback is that you won't be able to reuse the code for different files. To make it reusable, you'd have to take a metaprogramming approach, such that you create a script that generates a new shell script with the sources of whatever you want to be installed wherever you like.

IMO, the whole thing is totally absurd, as a .tar.gz with a Makefile would be enough, but well, your boss is your boss. Moreover, the whole thing seems like poorly reinventing a .deb-like "installer"... Maybe a .deb could be a solution if it happens to be a Debian-like OS (or a .rpm, if it's Red Hat-based).
Well, great thank you for pointing two solution for me. While, the files to be tared is not only phh files, maybe several folders with a lot of files.
And, as I have mentioned, the target machine environment maybe unknown, maybe it will not support perl, and let alone "*.deb" installer:)
I am reading this URL:[http://www.daniweb.com/forums/thread285988.html](http://www.daniweb.com/forums/thread285988.html), maybe it could help me.

---

### Post by huangyingw on 2010-06-07
> **lostinxlation said:**
> I don't know about PHP , but can't you just have a separate binary file(tar.gz) which is downloadable ?
If you want to include the binary archives in a file, uuencode/uudecode is the only way, as far as I know.. That's how email/usenet could accommodate the binary data in it long long long time ago.
hey, see these, they are near my goals now:)
```

#!/bin/bash
for i
do
echo "cat >$i <<'End of $i'"
cat $i
echo "End of $i"
done

```

```

./install.sh temp.tar.bz2>"new.sh"
rm -fv temp.tar.bz2
chmod 777 "new.sh"
./"new.sh"
#rm -fv new.sh

```

---

### Post by huangyingw on 2010-06-15
> **prshah said:**
> Unfortunately, there is no way to "attach" a binary file to a script without converting it to ASCII text. To convert, you need to use uuencode and uudecode. 

If you cannot access the programs, you can write your own uuencode/uudecode scripts. I've never done it, but I think it should be relatively easy. Use the [source code]("http://people.sc.fsu.edu/~burkardt/c_src/uuencode/uuencode.html") for hints.

You can also take a look at [makeself]("http://megastep.org/makeself/") which seems to have a custom way to integrate binary files into a shell script.
Great thank you for not only pointing out the root cause, but also a most convinient and easy solution of makeself

---

