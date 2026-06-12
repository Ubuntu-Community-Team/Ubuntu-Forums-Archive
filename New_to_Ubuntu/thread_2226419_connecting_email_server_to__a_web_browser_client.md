---
title: "connecting email server to  a web browser client"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by shad2 on 2014-05-27
How can i connect a local email server to a web browser interface and retrieve emails?
Any tutorials on this are  welcome.

---

### Post by brantcgardner on 2014-05-27
I would suggest you look at one of the available webmail packages, such as [SquirrelMail]("http://squirrelmail.org/"), they can do what you are describing.

---

### Post by sandyd on 2014-05-27
> **shad2 said:**
> How can i connect a local email server to a web browser interface and retrieve emails?
Any tutorials on this are  welcome.

You will want a web-email client.

Some examples are horde, and roundcube

---

### Post by shad2 on 2014-05-28
thanks for your answers,but can't i  just connect to the mailserver.I  have tried and still am trying just to connect to it from php.All iam  getting is:

**Warning**:  imap_open() [[function.imap-open]("http://localhost/function.imap-open")]: Couldn't open stream {localhost:143} in **/home/bal/tec/conn.php** on line **8**
[h=1]FAILED TO CONNECT TO IMAP HOST![/h]atleast i should be able to see the good connection result before i even go in to  horde or orundcube.
here is my test file:
<?php
$host="{localhost:143}";
$user="aretab@ba.localhost";
$pass="get4";
 
if ($mbox=imap_open( $host, $user, $pass ))
{
$imap_obj = imap_check($mbox);
echo "<h1>CONNECTED TO IMAP HOST</h1><h2>$host (".  $imap_obj->Nmsgs  .")<h2>";
} else
{
echo "<h1>FAILED TO CONNECT TO IMAP HOST!</h1>\n";
die;
}
 
echo "<h3>IMAP LIST OF FOLDERS</h3>";
$folders = imap_list($mbox, $host, "*");
echo "<ul>";
foreach ($folders as $folder) {
echo  '<li><a href="mail.php?folder=' . $folder .  '&func=view">' . imap_utf7_decode($folder) .  '</a></li>';
}
echo "</ul>";
imap_close($mbox);
?>

If i can be able to send mail to new users in the database on the terminal,why am i failing to atleast connect via php??

---

### Post by SeijiSensei on 2014-05-28
First, are you running **dovecot-imapd** on this host to handle IMAP connections?

If so, try running the command "telnet localhost 143".  Can you connect to dovecot that way?  If not, edit /etc/dovecot/dovecot.conf and remove the hash mark from this line:
```
listen = *, ::
```
then restart dovecot with "sudo service dovecot restart" and try the telnet test again.

If you only intend to connect to the IMAP server on localhost (which is common if the webmail client is on the same machine as the mail server), then you can use 
```
listen = 127.0.0.1
```
for greater security.

---

### Post by shad2 on 2014-05-29
hello [ ]("http://ubuntuforums.org/member.php?u=698195")[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") this is the result:
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE STARTTLS AUTH=PLAIN AUTH=LOGIN] Dovecot ready.
a login aretab getin1234     
a NO [AUTHENTICATIONFAILED] Authentication failed.

why is it that i cannot log in to the account  yet that is what it is in the database??And i can see it in the vmail folder

---

### Post by SeijiSensei on 2014-05-29
You don't have authentication set up correctly for dovecot it appears.  I never use databases for email accounts; I just give the users regular Unix accounts.  So I'm afraid I cannot help much more with this.

You should make sure that you have either **dovecot-mysql** or **dovecot-pgsql** installed.  These packages build the interface between dovecot and either MySQL or PostgreSQL respectively.

---

### Post by shad2 on 2014-05-30
Oh Seiji sesei,before you  let go.
this is what i have in my dovecot.conf file around that point
  protocol imap {
#     listen = *:10143
    listen =*:143
#     ssl_listen = *:10943
    ssl_listen =*:993
#     ..
   }
   protocol pop3 {
    listen = *:110
        ssl_listen = *:995
#     listen = *:10100
#     ..
      pop3_uidl_format = %08Xu%08Xv
   }
#   protocol managesieve {
#     listen = *:12000
#     ..
#   }
listen = *


And when I uncommented the listen as you said  and tried to restart dove cot ,it said
 * Restarting IMAP/POP3 mail server dovecot                                     If you have trouble with authentication failures,
enable auth_debug setting. See [http://wiki.dovecot.org/WhyDoesItNotWork](http://wiki.dovecot.org/WhyDoesItNotWork)
This message goes away after the first successful login.
Fatal: listen(0.0.0.0, 2000) failed: Address already in use
                                                                         [fail]

---

### Post by SeijiSensei on 2014-05-30
Did you enable auth_debug?  Did you try the solutions in that linked page?

---

### Post by shad2 on 2014-05-31
yes Seijisensei, Guess what! I decided to redo all the dovecot configuration file.This time i got this error in my erorr logs:
May 31 12:45:39 bal-laptop dovecot: auth-worker(default): sql(aretab@bal-laptop.localhost,127.0.0.1): Unknown scheme SHA512-CRYPT

Can't I use this with dovecot on ubuntu 10.04 ??
by the way is there b crypt for dovecot and how can i enforce that sort of scheme?

---

### Post by shad2 on 2014-06-01
Thanks seijisensei,all your ideas were good and led me to the solution I later changed thhe scheme to plain text ..

---

