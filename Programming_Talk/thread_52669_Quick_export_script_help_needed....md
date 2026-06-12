---
title: "Quick export script help needed..."
date: 2005-07-28
forum: Programming Talk
---

### Post by MikeyXX on 2005-07-28
Hi, I don't want to put my http_proxy and ftp_proxy environment variables in to run everytime someone logs in. I want the ability to run a script when I need the proxy changed. How would I do it? I currently run:

export http_proxy="blahblahblah" 

at the prompt and then again for the ft_proxy. I thought I could put each of these in a file and then rightclick and make it executable and then run sh proxy.sh or something and have it work. When I do, I get no response (which is normal) but it doesn't actually export it to an environmental variable, I think it's just doing so for it's session. Any suggestion?

---

### Post by LordHunter317 on 2005-07-28
Yeah, put the variables in your ~/.bashrc so they're global to every shell you run.

Otherwise, you'll have to type them in manually.

You can write a script containing the commands and source it to have it affect the current running shell, but that won't affect other processes.

---

### Post by MikeyXX on 2005-07-28
[QUOTE=LordHunter317]Yeah, put the variables in your ~/.bashrc so they're global to every shell you run.

Otherwise, you'll have to type them in manually.

You can write a script containing the commands and source it to have it affect the current running shell, but that won't affect other processes.[/QUOTE]
 I'm ok with the script. I knew about the bashrc, but I use my machine mostly where there is no proxy. How could I script the commands so I don't have to manual put them in?

---

### Post by cwaldbieser on 2005-07-28
The short answer is you can't.  You can only export shell variables to child processes.  The closest you could do would be to have a script with the export commands in it, and then just "$ source your_init_script".  Then command you run from that shell would have the proxy variables exported to it.

Another way might be to set up your login shell to bring up a menu that lets you choose whether or not to set those values when you log in.  You would have to makes sure it only happens for an interactive shell, though...

---

### Post by MikeyXX on 2005-08-02
[QUOTE=cwaldbieser]The short answer is you can't.  You can only export shell variables to child processes.  The closest you could do would be to have a script with the export commands in it, and then just "$ source your_init_script".  Then command you run from that shell would have the proxy variables exported to it.

Another way might be to set up your login shell to bring up a menu that lets you choose whether or not to set those values when you log in.  You would have to makes sure it only happens for an interactive shell, though...[/QUOTE]
 menu idea is a good one. Is there a website that would be good to walk me though how to set up a menu option? I can do it in a .cmd in windows, but I don't know what it would be here.

---

### Post by cwaldbieser on 2005-08-02
[QUOTE=MikeyXX]menu idea is a good one. Is there a website that would be good to walk me though how to set up a menu option? I can do it in a .cmd in windows, but I don't know what it would be here.[/QUOTE]

This site looks OK: [http://wiki.sblug.org/Bash_Menu_Program](http://wiki.sblug.org/Bash_Menu_Program) 

You want to make sure that this menu would only be started for an interactive shell.  I am not 100% certain off the top of my head, but I think you would want to run the menu from your ~/.bash_profile or ~/.bash_login file.

If you want to get really fancy, you could even try to do a graphical front end if you detect an X display.  This could be done with python & Tkinter or even maybe a shell script and Xmessage.

A simple console menu is the ideal fallback, though.  It works just about everywhere.

---

