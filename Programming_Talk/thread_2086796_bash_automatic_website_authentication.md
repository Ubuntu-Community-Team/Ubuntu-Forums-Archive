---
title: "bash automatic website authentication"
date: 2012-11-21
forum: Programming Talk
---

### Post by e64462 on 2012-11-21
Hello all,

I'm on a campus network, and they use Cisco Clean Access (NAC) to force users to authenticate via a web interface. This is fine for my desktop, but I'm also operating a separate file server (which is often not immediately available for me to login and authenticate on). I'm looking to automate the process somehow, probably by cron job, but I'd first like to get some code going that automatically authenticates my computer with Cisco's NAC web interface. I've tried several methods (curl, wget, various php scripts I edited from online)... nothing has even remotely worked. I believe this is possible because I found this:
> [http://hints.macworld.com/article.php?story=20060506184128453](http://hints.macworld.com/article.php?story=20060506184128453)post on a MAC forum, and several very general curl and wget examples online where people have accomplished similar things, but I've been unable to edit them for my needs. I've accessed the page source to the Cisco NAC login webpage; the relevant part seems to be:

```
<form method="post" name="loginform" action="../auth/perfigo_cm_validate.jsp" target="_parent">
        <div align="center">
            <input type="hidden" name="reqFrom" value="perfigo_login.jsp"/>
            <input type="hidden" name="uri" value=""/>
            <input type="hidden" name="cm" value=""/>
            <input type="hidden" name="userip" value="xxx.xxx.xxx.xxx"/>
            <input type="hidden" name="session" value=""/>
            <input type="hidden" name="pm"/>
            <input type="hidden" name="index" value="0"/>
            <input type="hidden" name="pageid" value="-1"/>
            <input type="hidden" name="compact" value="false"/>
         
    <input type="hidden" name="registerGuest" value="NO"/>
            <input type="hidden" name="userNameLabel" value="netID"/>
            <input type="hidden" name="passwordLabel" value="Password"/>
            <input type="hidden" name="guestUserNameLabel" value="Guest ID"/>
            <input type="hidden" name="guestPasswordLabel" value="Password"/>
            
            <table id='loginTable' cellspacing='8' class='loginForm'>
<tr><td id='userNameCell' align='right'>netID</td><td align='left'><input type='text' name='username' size='15' /></td></tr>
<tr><td id='passwordCell' align='right'>Password</td><td align='left'><input type='password' name='password' size='15' value=''/></td></tr>
<tr><td><input type='hidden' name='provider' value='netID Login'/></td></tr>
<tr><td colspan='2' align='center'><input type='submit' value='Continue'></td></tr>
</table>
</div>
```Any help you can provide would be MUCH appreciated.

---

### Post by slavik on 2012-11-22
look into curl/wget to submit the form.

another thing to look at is wwww::mechanize (perl library)

---

### Post by e64462 on 2013-01-13
If I find an answer I'll post back here for you. Best of luck!

e

---

