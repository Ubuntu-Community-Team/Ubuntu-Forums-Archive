---
title: "[SOLVED] number dictionary for aircrack ng ?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by cosine352 on 2008-10-01
Hi friends,
I was having fun cracking my wireless key. It was real easy when it was WEP. Now I have changed it to WPA. I got the .cap file with WPA handshake data. Now I am having problem cracking it.
The problem is with the dictionary I think. I know my passphrase is only numbers. But the dictionary I have is for words. Do anyone know about some good dictionary for numbers. It will be cool.

Thanks

---

### Post by vantsochev on 2008-10-01
I am not sure but you can try this:

[http://www.remote-exploit.org/codes_wyd.html](http://www.remote-exploit.org/codes_wyd.html)

---

### Post by Thelasko on 2008-10-01
> **cosine352 said:**
> It was real easy when it was WEP. Now I have changed it to WPA. I got the .cap file with WPA handshake data. Now I am having problem cracking it.
That's why people use WPA, it's significantly more secure.  If you are having trouble cracking your WPA it simply means your passphrase is random enough to not be vulnerable to a [dictionary attack]("http://en.wikipedia.org/wiki/Dictionary_attack").

The people in the [security section]("http://ubuntuforums.org/forumdisplay.php?f=338") of the forums can probably provide more information.

---

### Post by binbash on 2008-10-01
you will generate you own word list for john the ripper with [http://freshmeat.net/projects/wg/](http://freshmeat.net/projects/wg/)

example command : 

```

perl ./wg.pl -l 8 -u 64 -v abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWX YZ0123456789\`\~\!\@\#\$\%\^\&\*\(\\\_\+\=[]\;\'\,.\/\<\>\?\:\"\\}\|\ > mycraplist.txt 
```

---

### Post by cosine352 on 2008-10-01
Thanks binbash. that is really nice.

---

### Post by leigo na materia on 2009-01-01
> **binbash said:**
> you will generate you own word list for john the ripper with [http://freshmeat.net/projects/wg/](http://freshmeat.net/projects/wg/)

example command : 

```

perl ./wg.pl -l 8 -u 64 -v abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWX YZ0123456789\`\~\!\@\#\$\%\^\&\*\(\\\_\+\=[]\;\'\,.\/\<\>\?\:\"\\}\|\ > mycraplist.txt 
```

	
Hello to all

I am new staff in the Linux world and yet understand little of this.
My question is how do I install this application and then use the command to generate a list of words?
I tried but I can not!!

I await your help

---

### Post by leigo na materia on 2009-01-02
come on staff here give a hand.

please!

---

### Post by cosine352 on 2009-01-15
[http://digilander.libero.it/reda/downloads/perl/wg.pl]("http://digilander.libero.it/reda/downloads/perl/wg.pl") download this file and run the command (from the same directory as the file)
> perl ./wg.pl -l 8 -u 64 -v abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWX YZ0123456789\`\~\!\@\#\$\%\^\&\*\(\\\_\+\=[]\;\'\,.\/\<\>\?\:\"\\}\|\ > mycraplist.txt
in terminal. 

To open a terminal: Alt+F2 and then type > gnome-terminal

---

### Post by matteoredaelli on 2009-04-14
Ciao

I'm the author of wg.pl
it is an old perl script, it is not mainteined any more.
The new project for word generator (password cracks) is in Ruby and hosted by google. See [http://code.google.com/p/ruby-words-generators/](http://code.google.com/p/ruby-words-generators/)

Bye
[http://www.redaelli.org/matteo/](http://www.redaelli.org/matteo/)

---

### Post by flaflatas on 2009-04-16
> **matteoredaelli said:**
> Ciao

I'm the author of wg.pl
it is an old perl script, it is not mainteined any more.
The new project for word generator (password cracks) is in Ruby and hosted by google. See [http://code.google.com/p/ruby-words-generators/](http://code.google.com/p/ruby-words-generators/)

Bye
[http://www.redaelli.org/matteo/](http://www.redaelli.org/matteo/)


Ciao Matteo,

I know that I should also do my homework on this, but could you please give more detailed information, on how the installation is supposed to be made and how to use the program?

Gracie! :)

---

### Post by binbash on 2009-04-16
> **matteoredaelli said:**
> Ciao

I'm the author of wg.pl
it is an old perl script, it is not mainteined any more.
The new project for word generator (password cracks) is in Ruby and hosted by google. See [http://code.google.com/p/ruby-words-generators/](http://code.google.com/p/ruby-words-generators/)

Bye
[http://www.redaelli.org/matteo/](http://www.redaelli.org/matteo/)

Thanks for the new project!

---

