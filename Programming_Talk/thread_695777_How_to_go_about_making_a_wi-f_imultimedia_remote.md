---
title: "How to go about making a wi-f imultimedia remote"
date: 2008-02-13
forum: Programming Talk
---

### Post by chris1991 on 2008-02-13
Hello there. I am planning to create a simple program that will be able to control some of the multimedia aspects of mu Ubuntu 7.10 computer via a pocket pc.

My idea is to run Apache and create a basic site that will allow me to control the volume, play/pause and go next/previous from a simple web page.

I will then access this web page from my pocket pc and when I click on the link for pause, it will pause the current playing track on the computer over my wi-fi.

However, I only have programming knowledge in VB so this is my first linux programming project and I would apreiate any helo available.

Cheers,

 Chris

---

### Post by jsmiith on 2008-02-13
One simple way of doing this would be to write a simple PHP script for each action that runs a shell command with exec() and then redirects back to your menu page using your method of choice. 
I know that amarok allows you to pass arguments like --play and --previous so that would be pretty easy, not shure about rhythbox though.

---

### Post by chris1991 on 2008-02-14
Thank you for your reply. I am very familiar with PHP but I can not understand how it can be used to run a script on the local machine.

Another Idea that came up was to use a MySQL backend. I.e. the remote web page changes values in the database which is being read every second by the media player.

Thanks,

Chris

---

### Post by pedro_orange on 2008-02-14
Could try a webservice?

Then you can have an application running on your PocketPC that looked like a remote, and each button represents a Remote Procedure Call to the web service.

Then you can program it in whatever language you like.

---

### Post by jsmiith on 2008-02-14
You really can use any language you wish, I used PHP as an example because of its relative ease in setting up with apache. PHP, like most languages has functions that allow you to execute commands on the system hosting the script. e.g. system('cat /etc/fstab'); or exec('cat /etc/fstab'); would execute the command 'cat /etc/fstab' on the system the webserver is on.

---

### Post by t3hi3x on 2008-02-15
Agreed. That would probably be the best route. I would not suggest using a MySQL back end unless you had a daemon running that read those commands and passed them trough to the app. You could use cgi scripts.

How failure are you with C++?

EDIT:: lol i just saw your post about VB

Here's just a little pointer coming from experience. I used to be an avid Windows user. I became an expert if you will. I loved programming in my easy vb and it was good. But then I was introduced to t3h linux. One of the best things about linux is just about everything can be done via terminal, and the fact that the GUI (X) is simply a server running on top of linux is amazing for power.

What I'm trying to say is never assume you can't do it via commands, because chances are in some way you can. I will say to pull of a project like this I would suggest learning some type of OS based lanuage, whether it be C, Perl, Python, etc. This will allow you to hit linux APIs and all kinds of other stuff making projects like this more simple.

In the mean time:

in php you can create a link (button or text) that points to another PHP page.

ex. (index.php)

<?

//crap load of html (not really)

echo <a href "./pause.php">Pause</a>;

?>

(pause.php)

<?

exec(<script to tell program what to do>);

//go back to index

?>

make sense?

---

