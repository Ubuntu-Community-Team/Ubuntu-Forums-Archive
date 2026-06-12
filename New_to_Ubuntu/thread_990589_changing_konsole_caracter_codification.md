---
title: "changing konsole caracter codification"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by danex_ali on 2008-11-22
Hi people.
My konsole's default codification is UTF-8 but when i 'cat' a file that has special caracter's like à Ó ç (portuguese caracters), it doesn't show properly...
My question is simple: can i change the konsole's caracter codification without using gui?? In other words, is there a command to change the konsole's caracter codification?
In my case, i would like to change to iso 8859-1.
And then, if possible, return to the previous carater codification without using GUI's.
The reason is that im making a bash script that wget's a web pag, stores to a file.html with ">" , and then has to 'cat' it to my konsole.
the problem is that when it 'cats' caracters like À ó Ç ú .... it doesnt appear right... :S

Thank you in advance

---

### Post by cariboo on 2008-11-22
I don't know if this is quite what you are looking for, but when you have the terminal open go to View-->Character Encoding and select the encoding you want.

Jim

---

### Post by danex_ali on 2008-11-24
Yes, thats it. In my kubuntu (portuguese) it's Configuraçao(Configuration)>Codificação(Codification/Enconding)> then i choose the one that i want.
It's exactly that, but what i need is the command line to do that. I don't need the grafical way to do that.
Thanks for the reply Jim :)
still in need of help....

---

### Post by porchrat on 2008-11-24
You can change the encoding of the entire operating system by changing the locales.

This guide applies to Fiesty, but I don't see why it wouldn't work for hardy or intrepid as these sort of things tend not to change between releases.

[Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_locales_to_Ubuntu_the_command_line_way") is an example of how to do it.

---

### Post by danex_ali on 2008-12-01
Thank You porchrat, that really did the trick ;)
You forgot to mention that a reboot is nedeed after configurating the locales... but thanks a million =))

---

### Post by danex_ali on 2008-12-02
well, in fact, i was wrong porchrat. it did solve my problem but it raised a lot more than it solve... :(
Now i have some folder with odd names and in my adept, there are also a lot of odd caracters :(
The only thing that i need is to know the command line to change konsole's character codification. only that
thanks a lot for the efforts

---

