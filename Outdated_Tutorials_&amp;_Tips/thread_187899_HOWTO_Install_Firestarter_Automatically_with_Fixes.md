---
title: "HOWTO: Install Firestarter Automatically with Fixes"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by KrazyPenguin on 2006-06-03
This is how to start Firestarter Automatically at login, with Fixes to the administrative problems seen with Synaptic, Updater, etc.

This is not secure, but I have never heard of this to be a problem to anybody.

This section is copied out of my guide located here:
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Firestarter_.28Firewall.29](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Firestarter_.28Firewall.29)

I can not take full credit for this, except for simpifying the steps, editing, etc.

[I]**Note:** There was a problem with the word "DISPLAY" being displayed as "DI SPLAY".
The problem was due to a conflicion between the format of the line and the format of this forum.
I simply put **BOLD** text around the word "DISPLAY" to fix the problem.
[/I]
************************************************

 How to install Firestarter (Firewall)

    * Read #How to use this Guide
    * Read #How to add extra repositories 

sudo apt-get install firestarter

    * Read #How to refresh GNOME panel
    * Applications -> System Tools -> Firestarter 

    For more information please visit: [http://www.fs-security.com/](http://www.fs-security.com/) 


How to minimize Firestarter to a panel icon when closed

    * With Firestarter already opened
    * Preferences -> Check "Enable tray icon" -> Accept 


How to make Firestarter start automatically at startup

    * System -> Preferences -> Sessions -> Startup Programs -> Add 

sudo firestarter --start-hidden

    * Press "OK" 


How to have Firestarter start without the root password

    Note: This is not secure 

export EDITOR=gedit
sudo visudo

    * navigate to the # Defaults section
    * and place a # in front of this line Defaults !lecture,tty_tickets,!fqdn
    * so it looks like this: 

#Defaults !lecture,tty_tickets,!fqdn

    * then add this line right after it: 

Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="**DISPLAY** HOME XAUTHORIZATION"

    * At the very bottom of the file add this line: 

your_user_name ALL= NOPASSWD: /usr/sbin/firestarter

    * Save the file
    * Next we must fix the problem with adminstative applets that won't open due to the changes that we made to our visudo file
    * These applets include Synaptic and the Updater, and after entering your password they no longer open
    * For the next two lines, USERNAME = your username 

sudo ln -fs /home/USERNAME/.Xauthority /root/.Xauthority
sudo chown USERNAME.root /home/USERNAME/.Xauthority

    * Restart your computer 

************************************************

Hope this helps somebody!!!
Good luck!!!

---

### Post by nwgray on 2006-06-05
You are the man (or woman as the case may be). This FINALLY fixed my issues with autostarting Firestarter and Synaptic not running. Thank you so much!!

---

### Post by KrazyPenguin on 2006-06-05
[QUOTE=nwgray]You are the man (or woman as the case may be). This FINALLY fixed my issues with autostarting Firestarter and Synaptic not running. Thank you so much!![/QUOTE]

No problem.  Like I said somewhere, I cannot take full credit except for editing, and rewording etc.

Glad it help at least 1 person ;-)

Good luck!!!

The KrazyPenguin

---

### Post by xXx 0wn3d xXx on 2006-06-05
Thanks for posting this :) it worked really well.

---

### Post by skafiskafnjak on 2006-06-06
If im using SSH to install firestarte on remote PC what should I do to avoid to lock server, so that firewall is not blocking me to access server?

---

### Post by User-007 on 2006-06-06
Hi,

This doen't work with me. When completed all the tasks above and restarted, the firestarter won't open. Furthermore i'll get this: 

--------------------------------------------------------------------------------------------
$ sudo firestarter

(firestarter:5526): Gtk-WARNING **: cannot open display:

--------------------------------------------------------------------------------------------

Same problem occurs when trying to start anything with "sudo":

---------------------------------------------------------------------------------------------
$ sudo gedit /etc/sudoers 
cannot open display: (null) 
Run 'gedit --help' to see a full list of available command line options. 

---------------------------------------------------------------------------------------------

Now I am really on stuck. Please someone help me to get this solved.

Thanks!
User JB

---

### Post by phase on 2006-06-06
Nice, that work.

---

### Post by User-007 on 2006-06-06
Hey, plz help me to solve this. See above.

User JB

---

### Post by oyvindaa on 2006-06-06
```
sudo firestarter --start-hidden
```

This doesn't make Firestarter start automatically on my box.

Why is that?

---

### Post by suchyh on 2006-06-06
[QUOTE=User-007]Hi,

This doen't work with me. When completed all the tasks above and restarted, the firestarter won't open. Furthermore i'll get this: 

--------------------------------------------------------------------------------------------
$ sudo firestarter

(firestarter:5526): Gtk-WARNING **: cannot open display:

--------------------------------------------------------------------------------------------

Same problem occurs when trying to start anything with "sudo":


User JB[/QUOTE]

Hello User-007!

I followed the instructions in this thread..and I ended with the same problems as you! 
There is one typo-mistake in the instructions:
part of the line which should be added to visudo - "DISPLAY HOME XAUTHORIZATION"
and not "DI SPLAY HOME XAUTHORIZATION"

I repeated the whole procedure with this correction from the beginning and then restarted and now everything works!:D  Firestarter and Synaptic as well!

P.S.: you can check it at Krazy Penguins site: [http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_have_Firestarter_start_without_the_root_password](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_have_Firestarter_start_without_the_root_password)
as well!

Hynek

---

### Post by User-007 on 2006-06-06
Thanks a lot, 

I solved this also a couple of minutes ago, by correcting that typo. But thanks to original "author", Now all works like a charm.

User NB

---

### Post by KrazyPenguin on 2006-06-07
Just a kick note here.

a) The typo doesn't appear in my guide.
b) The typo doesn't appear when I go to edit it in these forums.

So this is really wierd :twisted: 

Anybody have any ideas why this exists???

Thanks.

---

### Post by Arktis on 2006-06-07
Thanks for this guide.  At first, it didn't work at all for me, after doing exactly as the guide says at each step.  But then I remembered something that helped determine the problem, and with that in mind, went back to 

**System > Preferences > Sessions > Startup Programs** 

and changed *sudo firestarter --start-hidden* to *sudo 'firestarter --start-hidden'*, and hit cntrl + alt + backspace to restart the x session.  

It worked; firestarter loaded up and showed in the systray.  But for some reason, the startup command had changed back to the initial *sudo firestarter --start-hidden*.

Strange.

---

### Post by suchyh on 2006-06-09
[QUOTE=KrazyPenguin]Just a kick note here.

a) The typo doesn't appear in my guide.
b) The typo doesn't appear when I go to edit it in these forums.

So this is really wierd :twisted: 

Anybody have any ideas why this exists???

Thanks.[/QUOTE]

Hello KrazyPenguin!
I know it's not in your guide. When I was writting my reply, I copied the right sequence from your site. Then I hit Preview Post and the "typo" appeared again..So the mistake is at the way how forum format and break messages..
Anyway thanks for great guide, it works!

---

### Post by bootleg on 2006-10-28
Still works with 6.10.

Thanks! :mrgreen: 

Maybe you have do add, that /etc/sudoers is read only, so you have to change that for editing the file.

---

### Post by Zaggy on 2006-10-28
Thanks for the guide!
And the hint from suchyh!

---

### Post by frogotronic on 2006-10-28
Hello,

  This completely worked for me!  Thank you for the excellent post to solve awhat had been a very annoying problem.

- CH

---

### Post by dashingdon on 2006-11-05
This guide rocks !!!! 

Thank You .. I was struggling with the GTK error. This worked like charm :)

-DD

---

### Post by Sgt. Pepper on 2006-11-06
I have this problem 
ik@ik-desktop:~$ sudo apt-get install firestarter
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
firestarter ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 2 no actualizados.
1 no instalados del todo o eliminados.
Necesito descargar 0B de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando firestarter (1.0.3-1.2ubuntu3) ...
 * Starting the Firestarter firewall...                                  [fail] 
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error al procesar firestarter (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone help me?

---

