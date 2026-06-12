---
title: "HELP Ruby!"
date: 2006-12-26
forum: Programming Talk
---

### Post by nick.inspiron6400 on 2006-12-26
I just installed Ruby. Again, how do i load the application? I have added this "Command Application  Launch" I type ruby...

NOTHING HAPPENS!!!

I really know nothing about Linux so please help me!

---

### Post by tikal26 on 2006-12-27
I thought tha ti had answered this questions for you already. I don't kow if you did not get to read it, but I think that you are confused. when you ask How do I load the application?
Ruby is not and application but a language. So  to create something with ruby I will do this

1. Install 
enable universe repositories
sudo apt-get install ruby irb rdoc

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ruby&searchon=names&subword=1&version=edgy&release=all&page=6&number=50](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ruby&searchon=names&subword=1&version=edgy&release=all&page=6&number=50)
The ruby pacakege install is 1.8.2
2. Test it 
You can do it so many ways
a.)you can open a shell and type irb and then Enter
    "hello wolrd"
     enter
you should get a hello world
b.) or open your favorite text editor 
     Type  puts ' Hello World'
      Save it as helloworld.rb
      from the command line type  Ruby helloworld.rb
      your should get  hello world as output. 

I don't know if that answers your question, but if you could be a little bit more precise I am sure that we could help you.  Maybe what you want to install is rails in taht case 
sudo apt-get install rails
and you can take it from there

---

### Post by nick.inspiron6400 on 2006-12-27
Thanks for your reply.

1. How do i open the shell?
2. How do i get the command line open?

Thanks, but i only migrated from Windows a few days ago!

---

### Post by Ramses de Norre on 2006-12-27
The terminal should be somewhere in Applications > system tools or something when using gnome. When you've got kde you'll need to look in your menu for Konsole.

---

### Post by tikal26 on 2006-12-27
I use kde so you can use konsole for the shell and command line part of the instructions. 
I don't know where they are on gnome. You can also apt-get install yakuake and then you can type  f12 and it appears on the top. I like to use that so that I can  still use it and make it appear and  dissapear any time
[http://www.kde-look.org/content/preview.php?preview=1&id=36660&file1=36660-1.png&file2=&file3=&name=Yakuake+for+Kubuntu](http://www.kde-look.org/content/preview.php?preview=1&id=36660&file1=36660-1.png&file2=&file3=&name=Yakuake+for+Kubuntu)

I am sorry that I can't be of more help with gnome, but I trie looking up the wiki and it was slaw so maybe later I can look that up.

---

