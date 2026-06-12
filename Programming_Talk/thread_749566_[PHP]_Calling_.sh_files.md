---
title: "[PHP] Calling .sh files"
date: 2008-04-08
forum: Programming Talk
---

### Post by itsbmw on 2008-04-08
ok so i am running a game server for a friend. it uses java and i made a simple control panel with HTML. 
here is the page source : ```

<html><head><title>Dylan's Control Panel
</title></head><body>

<h1>RuneScape Server on haze-linux</h1>

<FORM METHOD="LINK" ACTION="compile.php">
<INPUT TYPE="submit" VALUE="Compile">
</form>
<br>
<FORM METHOD="LINK" ACTION="run.php">
<INPUT TYPE="submit" VALUE="Run">
</form>
<br>
<FORM METHOD="LINK" ACTION="stop.php">
<INPUT TYPE="submit" VALUE="Stop">
</form>

</body></html>
```

my compile.php :
[PHP]<?php
shell_exec('/home/haze/rs/compile.sh > dev/null/ 2>&1');
?>[/PHP]
Start and stop.php look the same but with run.sh and stop.sh.
my run.sh:
```
#!/bin/sh
cd /home/haze/rs/
java server
```
my stop.sh
```
#!/bin/sh
cd /home/haze/rs/
kill $(pgrep java)
killall -v java
pkill java
kill `ps -ef | grep java | grep -v grep | awk '{print $2}'`
```
my compile.sh :
```
#!/bin/sh
cd /home/haze/rs/
javac *java
```
When i hit the buttons on the control panel they load the php page up no errors. But nothing happens on the server. I have tested the compile/stop/run scripts from terminal and they work perfect.
My question is what do i do to call these files? Any help is appreciated. I am not a PHP wiz but it is a very helpful language.
EDIT: Should i maybe make these files CGI and put them in my webs cg-bin directory?

---

### Post by wrightee on 2008-04-08
Make sure the .sh is executable, edit sudoers accordingly (sorry, don't have ref to hand and out of battery in 4 mins) and run thus:

[PHP]
$output = shell_exec('sudo /var/www/blah.sh');
#echo "<pre>$output</pre>";
[/PHP]    

..works for me.. I call that kind of thing with an ajax call, lets me grab the output and shove it back into a div on the page to see what's going on.

Your prob is most likely in the permissions I would guess.. Hope that helps!

---

### Post by itsbmw on 2008-04-08
Great thank you. So i should just run it as sudo? But if it wants a pass then what? I already set the chmod so... I also can run the script without sudo or root. when i get back on my machine i will test that. 


EDIT : Would i put this in a CGI?

---

### Post by wrightee on 2008-04-09
I don't run it as a cgi - when I set it up I remember all the challenge was in the sudoers edit part - I only ran mine as sudo since the script did a few tricky things that needed big permissions so to speak, it might not be necessary.  Start by echo'ing $output and seeing what it says, that'll probably give you the biggest clue.

---

### Post by itsbmw on 2008-04-09
ok thanks illl try that when i get home.

---

