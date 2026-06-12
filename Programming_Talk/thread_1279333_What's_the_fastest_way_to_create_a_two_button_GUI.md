---
title: "What's the fastest way to create a two button GUI?"
date: 2009-09-30
forum: Programming Talk
---

### Post by NinjaNumberNine on 2009-09-30
Well, basically I want a program that looks like the first screenshot (that isn't an actuall program, just edited another screenshot) and it needs to do the following:
If the first button is clicked, it will run the following script:

```
#! /bin/bash
mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf
```And when the second button is pressed,

```
!#/bin/bash

killall mplayer
```(Please let me know if there is a more efficient way of stopping just that "mplayer" from recording)

If you know more about programming than I do, (almost nothing :) ) please reply!

Thanks!


NinjaNumberNine


EDIT: sorry, forgot the screenshot, I'm working on it!

---

### Post by days_of_ruin on 2009-09-30
There is a program just for this purpose, zenity. ```
man zenity
```

---

### Post by NinjaNumberNine on 2009-09-30
Do they have a GUI for doing it? I am not a good programmer.. Here's the original thread. [http://ubuntuforums.org/showthread.php?t=1245479&page=1]("http://ubuntuforums.org/showthread.php?t=1245479&page=3")

---

### Post by Tony Flury on 2009-09-30
The point is - if you had looked at the man pages for zenity as suggested - is that zenity is a simple way of creating GUIs from bash scripts.

so you could relatively simply write a bash scriot that creates a GUI exactly as you required, and where the buttons do exactly what you want them to do.

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> Do they have a GUI for doing it? I am not a good programmer.. Here's the original thread. [http://ubuntuforums.org/showthread.php?t=1245479&page=1]("http://ubuntuforums.org/showthread.php?t=1245479&page=3")

nope. i don't have mplayer so untested:

```

#!/bin/sh
read=`zenity --list --title='Stream Recorder' --column=Action Record Stop`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf
fi

if [ $read = "Stop" ]; then
 killall mplayer
fi


```

---

### Post by NinjaNumberNine on 2009-09-30
What's that, a script?
I ran it as one and it showed screenshot one. I tried double-clicking the buttons and it does something apparently, but I don't know where it puts the output file.

---

### Post by NinjaNumberNine on 2009-09-30
> **Tony Flury said:**
> The point is - if you had looked at the man pages for zenity as suggested - is that zenity is a simple way of creating GUIs from bash scripts.

so you could relatively simply write a bash scriot that creates a GUI exactly as you required, and where the buttons do exactly what you want them to do.
I see. I had looked at the man pages first thing, just wondered if they had a GUI frontend for Zenity.

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> What's that, a script?

yup, a zenity script that does what you asked it to do.

run this part:
**zenity --list --title='Stream Recorder' --column=Action Record Stop**

in a terminal to see what it looks like.

i'll do a xmessage 1 in a minute, which is more of the button look.

---

### Post by kerry_s on 2009-09-30
using xmessage:

```

#!/bin/sh
read=`xmessage -fn 9x15 -g -5+10 "Stream Recorder" -buttons Record,Stop,Cancel -print`

if [ $read = "Record" ]; then
mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf
fi

if [ $read = "Stop" ]; then
 killall mplayer
fi

if [ $read = "Cancel" ]; then
	exit 0
fi

```

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> What's that, a script?
I ran it as one and it showed screenshot one. I tried double-clicking the buttons and it does something apparently, but I don't know where it puts the output file.

create folder named "bin" in your home folder, put your scripts in there. log out & back in. then create your launcher.

i just modified my scripts to do what you want.

---

### Post by days_of_ruin on 2009-09-30
See the attached script.

To run it:```
chmod +x test.sh
./test.sh
```

---

### Post by NinjaNumberNine on 2009-09-30
What in the world does that do? I read scripts before executing. :)

---

### Post by NinjaNumberNine on 2009-09-30
> **kerry_s said:**
> yup, a zenity script that does what you asked it to do.
i'll do a xmessage 1 in a minute, which is more of the button look.
That looks great, is there a way to take out the "Shutdown Options" thingy and maybe name the window differently? It's fine as it is, but I am something of a tweaker. :)
EDIT: Uh-oh, looks like something malfunctioned. When I click record in the xmessage dialog, the window shuts down and five of the screenshot 1 dialogs pop up.

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> That looks great, is there a way to take out the "Shutdown Options" thingy and maybe name the window differently? It's fine as it is, but I am something of a tweaker. :)

:lolflag: my bag, i fixed it to the "stream recorder" on your screenshot. sorry, still working on my first cup of coffee, not really awake yet.

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> That looks great, is there a way to take out the "Shutdown Options" thingy and maybe name the window differently? It's fine as it is, but I am something of a tweaker. :)
EDIT: Uh-oh, looks like something malfunctioned. When I click record in the xmessage dialog, the window shuts down and five of the screenshot 1 dialogs pop up.

are you running it as root?

---

### Post by NinjaNumberNine on 2009-09-30
> :lolflag: my bag, i fixed it to the "stream recorder" on your screenshot. sorry, still working on my first cup of coffee, not really awake yet.What time is it where you live? it's 6:19 PM here. :) (Seriously; I'm in Hot Springs, AR.)
Thanks for changing the script. Just one thing left- the window shuts down when you click record. I wish it would stay on until you told it to Stop.

EDIT: I was not running it as root, but when you edited the first script, it fixed something. Now there are no error messages. Good job! Still the problem with rapid shutdown, though.

---

### Post by NinjaNumberNine on 2009-09-30
And I STILL cant find where it's storing it... :(

---

### Post by kerry_s on 2009-09-30
> **days_of_ruin said:**
> See the attached script.

To run it:```
chmod +x test.sh
./test.sh
```

that does not work, did you try it?

---

### Post by NinjaNumberNine on 2009-09-30
> **kerry_s said:**
> that does not work, did you try it?
I did not, not knowing what it would do. All it had in it was a bunch of gibberish about Ubuntu Forums. Is it safe, and what would it do?

---

### Post by NinjaNumberNine on 2009-09-30
And is it REALLY morning there? :shock:

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> And I STILL cant find where it's storing it... :(

it would be in your home/you/recording.asf, if it's not then something is wrong with your command:
[B]mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf
[/B]

nothing can be done about the exit, there simple scripts.
i'm thinking maybe make it 2 part, for example: the first will just say "Record", that would run the script & open another window with "Stop". could you live with that? which 1 you want zenity or xmessage ?

it's 1:30pm here in hawaii, but i just went to bed at around 6:00am.

---

### Post by kerry_s on 2009-09-30
> **NinjaNumberNine said:**
> I did not, not knowing what it would do. All it had in it was a bunch of gibberish about Ubuntu Forums. Is it safe, and what would it do?

dang you move fast, i was talking to the other guy.

---

### Post by days_of_ruin on 2009-09-30
> **kerry_s said:**
> that does not work, did you try it?

I did but it appears that the website the OP wants to record from is down.

As for what it does:

```
#!/usr/bin/env bash

### This uses zenity to create a popup window that asks
### the user what they want to do.
RES=`zenity --question --text="What do you want to do?" --cancel-label="Stop Recording" --ok-label="Start Recording"` 

### zenity returns a number based on what the user clicked
### 0 = Ok
### 1 = Cancel
### -1 = If the window was destroyed in some strange way.
case $? in
    0)  
### This is the command you gave to record
        `mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' \
        -dumpstream -dumpfile recording.asf `
        ;;  
    1)  
### This obviously kills mplayer.
        `killall mplayer`;;
    -1) 
        echo "no response";;
esac

```

---

### Post by NinjaNumberNine on 2009-09-30
> I did but it appears that the website the OP wants to record from is down.Whaddaya mean, I iz listening to it as I type. :mrgreen:
BTW How's Hawaii?

---

### Post by NinjaNumberNine on 2009-09-30
> it would be in your home/you/recording.asf That's what I thought, too, but it isn't. I have done this before and it dropped the file there like a good boy. :)

---

### Post by NinjaNumberNine on 2009-09-30
-And THIS is the ubuntuforums gibberish: (:))
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" dir="ltr" lang="en">
<head>
<meta name="robots" content="noindex,follow" />
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<meta name="generator" content="vBulletin 3.8.1" />

<meta name="keywords" content="ubuntu forums,ubuntu linux,ubuntu,linux forum,ubuntu forum,linux ubuntu,ubuntu support,ubuntu help,ubuntu linux help" />
<meta name="description" content="A help and support forum for Ubuntu Linux." />


<!-- CSS Stylesheet -->
<style type="text/css" id="vbulletin_css">
/**
* vBulletin 3.8.1 CSS
* Style: 'CleanV2'; Style ID: 98
*/
@import url("clientscript/vbulletin_css/style-6a8e21d1-00098.css");
</style>
<link rel="stylesheet" type="text/css" href="clientscript/vbulletin_important.css?v=381" />


<!-- / CSS Stylesheet -->

<script type="text/javascript" src="http://yui.yahooapis.com/2.6.0/build/yahoo-dom-event/yahoo-dom-event.js?v=381"></script>
<script type="text/javascript" src="http://yui.yahooapis.com/2.6.0/build/connection/connection-min.js?v=381"></script>
<script type="text/javascript">
<!--
var SESSIONURL = "";
var SECURITYTOKEN = "guest";
var IMGDIR_MISC = "images/misc";
var vb_disable_ajax = parseInt("0", 10);
// -->
</script>
<script type="text/javascript" src="clientscript/vbulletin_global.js?v=381"></script>



    <link rel="alternate" type="application/rss+xml" title="Ubuntu Forums RSS Feed" href="external.php?type=RSS2" />
    

<meta name="verify-v1" content="t926SUC4SSJh1e95C+UKAk9XhKuZbCP/ArLrracPVgw=" />
    <title>Ubuntu Forums</title>

</head>
<body>
<br />
<div align="center">
  <b class="vbclean_top">
  <b class="vbclean_top1"><b></b></b>
  <b class="vbclean_top2"><b></b></b>
  <b class="vbclean_top3"></b>
  <b class="vbclean_top4"></b>
  <b class="vbclean_top5"></b></b>

  <div class="vbclean_topfg">
</div>
<!-- logo -->
<a name="top"></a>
<table class="vbclean_topfg" border="0" width="99%" cellpadding="0" cellspacing="0" align="center">
<tr>
    <td class="vbclean_topfg" align="left"><a href="index.php?"><img src="http://ubuntuforums.org/images/misc/ubuntulogo.png" border="0" alt="Ubuntu Forums" /></a></td>
    <td class="vbclean_topfg" align="right" id="header_right_cell">
<a href="http://ubuntu.com">ubuntu.com</a> - <a href="http://launchpad.net">launchpad.net</a> - <a href="https://help.ubuntu.com/">ubuntu help</a>
<div id="searchbox">

                <form action="search.php?do=process" method="post">
                    <p>
                        <label for="q" accesskey="s"><span class="mnemonic">S</span>earch</label>
                        <input type="text" value="" name="query" id="q" />
                                <input type="hidden" name="s" value="27c321839c13d3b33ea04662fea2e9ed" />
    <input type="hidden" name="securitytoken" value="guest" />
                                <input type="hidden" name="do" value="process" />
                                <input type="hidden" name="forumchoice[]" value="" />
                                <input type="hidden" name="childforums" value="1" />
                                <input type="hidden" name="exactname" value="1" />
                        <button type="submit" name="op"><span>go</span></button>
                    </p> 
                </form>
            </div>
        &nbsp;
    </td>
</tr>
</table>
<!-- /logo -->

<!-- content table -->
<!-- open content container -->

<div align="center">
    <div class="page" style="width:99%; text-align:left">
        <div style="padding:0px 25px 0px 25px" align="left">




<div style="float:right;margin-top:20px" id="launchpad_login"><small>Or,
    <a href="launchpad_login.php">Sign in using your Launchpad ID</a></small></div>

<br />

<!-- breadcrumb, login, pm info -->
<table class="tborder" cellpadding="6" cellspacing="1" border="0" width="100%" align="center">
<tr>
    <td class="alt1" width="100%">
        
            <table cellpadding="0" cellspacing="0" border="0">
            <tr valign="bottom">
                <td><a href="#" onclick="history.back(1); return false;"><img src="images/misc/navbits_start.gif" alt="Go Back" border="0" /></a></td>
                <td>&nbsp;</td>
                <td width="100%"><span class="navbar"><a href="index.php?" accesskey="1">Ubuntu Forums</a></span> </td>
            </tr>
            <tr>
                <td class="navbar" style="font-size:10pt; padding-top:1px" colspan="3"><a href="/attachment.php?attachmentid=130303&amp;d=1254351087"><img class="inlineimg" src="images/misc/navbits_finallink_ltr.gif" alt="Reload this Page" border="0" /></a> <strong>
    vBulletin Message

</strong></td>
            </tr>
            </table>
        
    </td>

    <td class="alt2" nowrap="nowrap" style="padding:0px">
        <!-- login form -->
        <form action="login.php?do=login" method="post" onsubmit="md5hash(vb_login_password, vb_login_md5password, vb_login_md5password_utf, 0)">
        <script type="text/javascript" src="clientscript/vbulletin_md5.js?v=381"></script>
        <table cellpadding="0" cellspacing="3" border="0">
        <tr>
            <td class="smallfont"><label for="navbar_username">User Name</label></td>
            <td><input type="text" class="bginput" style="font-size: 11px" name="vb_login_username" id="navbar_username" size="10" accesskey="u" tabindex="101" value="User Name" onfocus="if (this.value == 'User Name') this.value = '';" /></td>
            <td class="smallfont" nowrap="nowrap"><label for="cb_cookieuser_navbar"><input type="checkbox" name="cookieuser" value="1" tabindex="103" id="cb_cookieuser_navbar" accesskey="c" />Remember Me?</label></td>
        </tr>
        <tr>
            <td class="smallfont"><label for="navbar_password">Password</label></td>
            <td><input type="password" class="bginput" style="font-size: 11px" name="vb_login_password" id="navbar_password" size="10" tabindex="102" /></td>
            <td><input type="submit" class="button" value="Log in" tabindex="104" title="Enter your username and password in the boxes provided to login, or click the 'register' button to create a profile for yourself." accesskey="s" /></td>
        </tr>
        </table>
        <input type="hidden" name="s" value="27c321839c13d3b33ea04662fea2e9ed" />
    <input type="hidden" name="securitytoken" value="guest" />
        <input type="hidden" name="do" value="login" />
        <input type="hidden" name="vb_login_md5password" />
        <input type="hidden" name="vb_login_md5password_utf" />
        </form>
        <!-- / login form -->
    </td>

</tr>
</table>
<!-- / breadcrumb, login, pm info -->
<div>
  <b class="vblcean_navbar">
  <b class="vblcean_navbar1"><b></b></b>
  <b class="vblcean_navbar2"><b></b></b>
  <b class="vblcean_navbar3"></b>
  <b class="vblcean_navbar4"></b>
  <b class="vblcean_navbar5"></b></b>

  <div class="vblcean_navbarfg">

<!-- nav buttons bar -->
    <table cellpadding="0" cellspacing="0" border="0" width="100%" align="center">
    <tr align="center">
        
        
            <td class="vbclean_navbar_bg"><a href="register.php?" rel="nofollow">Register</a></td>
<td class="vbclean_navbar_bg"><a href="http://ubuntuforums.org/login.php?do=lostpw" rel="nofollow">Reset Password</a></td>
        

        
        
        <td id="helpmenu" class="vbclean_navbar_bg"><a href="#helpmenu">Forum Help</a> <script type="text/javascript"> vbmenu_register("helpmenu"); </script></td>
    <td id="fcmenu" class="vbclean_navbar_bg"><a href="#fcmenu">Forum Council</a> <script type="text/javascript"> vbmenu_register("fcmenu"); </script></td>
        
            
                <td class="vbclean_navbar_bg"><a href="search.php?" accesskey="4">Search</a></td>
                
                <td class="vbclean_navbar_bg"><a href="search.php?do=getdaily" accesskey="2">Today's Posts</a></td>
                
            
            <td class="vbclean_navbar_bg"><a href="forumdisplay.php?do=markread" rel="nofollow">Mark Forums Read</a></td>
            
        
        
        
        </tr>
    </table>
<!-- / nav buttons bar -->
</div>

  <b class="vblcean_navbar">
  <b class="vblcean_navbar5"></b>
  <b class="vblcean_navbar4"></b>
  <b class="vblcean_navbar3"></b>
  <b class="vblcean_navbar2"><b></b></b>
  <b class="vblcean_navbar1"><b></b></b></b>
</div>

<br />








<div class="vbmenu_popup" id="helpmenu_menu" style="display:none">
    <table cellpadding="4" cellspacing="1" border="0">
    <tr><td class="thead">Ubuntu Forums Help</td></tr>    
    <tr><td class="vbmenu_option"><a href="http://ubuntuforums.org/index.php?page=about">About Ubuntu Forums</a></td></tr>
    <tr><td class="vbmenu_option"><a href="http://ubuntuforums.org/index.php?page=policy">Ubuntu Forums Code of Conduct</a></td></tr>
    <tr><td class="vbmenu_option"><a href="http://ubuntuforums.org/announcement.php?f=48">Forum FAQ</a></td></tr>

    </table>
</div>
<div class="vbmenu_popup" id="fcmenu_menu" style="display:none">
    <table cellpadding="4" cellspacing="1" border="0">
    <tr><td class="thead">Forum Council Information</td></tr>    
    <tr><td class="vbmenu_option"><a href="https://wiki.ubuntu.com/ForumCouncil">Who we are</a></td></tr>
    <tr><td class="vbmenu_option"><a href="https://wiki.ubuntu.com/ForumCouncilAgenda">Forum Council Agenda</a></td></tr>
    <tr><td class="vbmenu_option"><a href="https://wiki.ubuntu.com/ForumsGovernance">Forum Governance</a></td></tr>

    </table>
</div>




<table class="tborder" cellpadding="6" cellspacing="1" border="0" width="70%" align="center">
<tr>
    <td class="tcat">vBulletin Message</td>
</tr>
<tr>
    <td class="panelsurround" align="center">
    <div class="panel">
        <div align="left">

        
            <script type="text/javascript" src="clientscript/vbulletin_md5.js?v=381"></script>
            <form action="login.php?do=login" method="post" onsubmit="md5hash(vb_login_password, vb_login_md5password, vb_login_md5password_utf, 0)">
            <input type="hidden" name="do" value="login" />
            <input type="hidden" name="url" value="/attachment.php?attachmentid=130303&amp;d=1254351087" />
            <input type="hidden" name="vb_login_md5password" />
            <input type="hidden" name="vb_login_md5password_utf" />
            

            <input type="hidden" name="s" value="27c321839c13d3b33ea04662fea2e9ed" />
            <input type="hidden" name="securitytoken" value="guest" />

            <!-- permission error message - user not logged in -->


            <div class="smallfont">You are not logged in or you do not have permission to access this page. This could be due to one of several reasons:</div>

            <ol>
                <li class="smallfont">You are not logged in. Fill in the form at the bottom of this page and try again.</li>
                <li class="smallfont">You may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?</li>
                <li class="smallfont">If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.</li>
            </ol>

            <fieldset class="fieldset">
                <legend>Log in</legend>
                <table cellpadding="0" cellspacing="3" border="0" align="center">
                <tr>
                    <td>User Name:<br /><input type="text" class="bginput" name="vb_login_username" size="50" accesskey="u" tabindex="1" /></td>
                </tr>
                <tr>
                    <td>Password:<br /><input type="password" class="bginput" name="vb_login_password" size="50" tabindex="1" /></td>
                </tr>
                <tr>
                    <td>
                        <span style="float:right"><a href="login.php?do=lostpw">Forgotten Your Password?</a></span>
                        <label for="cb_cookieuser"><input type="checkbox" name="cookieuser" value="1" id="cb_cookieuser" tabindex="1" />Remember Me?</label>
                    </td>
                </tr>
                <tr>
                    <td align="right">
                        <input type="submit" class="button" value="Log in" accesskey="s" tabindex="1" />
                        <input type="reset" class="button" value="Reset Fields" accesskey="r" tabindex="1" />
                    </td>
                </tr>
                </table>
            </fieldset>

            <div class="smallfont">The administrator may have required you to <a href="register.php?do=signup">register</a> before you can view this page.</div>
            </form>

            <!-- / permission error message - user not logged in -->
        

        </div>
    </div>
    <!--
    <div style="margin-top:6px">
        <input type="submit" class="button" value="Go Back" accesskey="s" onclick="history.back(1); return false" />
    </div>
    -->
    </td>
</tr>
</table>

<br />


<!-- forum jump -->
<table cellpadding="0" cellspacing="0" border="0" align="center">
<tr>
    <td><div class="smallfont" style="text-align:left; white-space:nowrap">
    <form action="http://ubuntuforums.org/forumdisplay.php" method="get">
    <input type="hidden" name="s" value="27c321839c13d3b33ea04662fea2e9ed" />
    <input type="hidden" name="daysprune" value="" />
    <strong>Forum Jump</strong><br />
    <select name="f" onchange="this.form.submit();">
        <optgroup label="Site Areas">
            <option value="cp" >User Control Panel</option>
            <option value="pm" >Private Messages</option>
            <option value="subs" >Subscriptions</option>
            <option value="wol" >Who's Online</option>
            <option value="search" >Search Forums</option>
            <option value="home" >Forums Home</option>
        </optgroup>
        
        <optgroup label="Forums">
        <option value="130" class="fjdpth0" > The Ubuntu Forum Community</option>
<option value="326" class="fjdpth1" >&nbsp; &nbsp;  Absolute Beginner Talk</option>
<option value="327" class="fjdpth1" >&nbsp; &nbsp;  Main Support Categories</option>
<option value="331" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  General Help</option>
<option value="329" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Desktop Environments</option>
<option value="328" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Apple Users</option>
<option value="333" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Installation &amp; Upgrades</option>
<option value="334" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Multimedia &amp; Video</option>
<option value="343" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  x86 64-bit Users</option>
<option value="332" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Hardware &amp; Laptops</option>
<option value="335" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Multimedia Production</option>
<option value="342" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Dell Ubuntu Support</option>
<option value="338" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Security Discussions</option>
<option value="336" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Networking &amp; Wireless</option>
<option value="341" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  System76 Support</option>
<option value="339" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Server Platforms</option>
<option value="367" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu One</option>
<option value="376" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Moblin Remix</option>
<option value="325" class="fjdpth1" >&nbsp; &nbsp;  Forum Archive</option>
<option value="73" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Absolute Beginner Talk</option>
<option value="173" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Main Support Categories</option>
<option value="211" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Apple Intel Users</option>
<option value="133" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Apple PPC Users</option>
<option value="132" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Desktop Environments</option>
<option value="223" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Desktop Effects &amp; Customization</option>
<option value="131" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  General Help</option>
<option value="135" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Hardware &amp; Laptops</option>
<option value="140" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Installation &amp; Upgrades</option>
<option value="138" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Multimedia &amp; Video</option>
<option value="254" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Multimedia Production</option>
<option value="136" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Networking &amp; Wireless</option>
<option value="323" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Partner Repository</option>
<option value="322" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Security Discussions</option>
<option value="7" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Server Platforms</option>
<option value="146" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Sun Sparc Users</option>
<option value="158" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  System76 Support</option>
<option value="256" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Dell  Ubuntu Support</option>
<option value="134" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  x86 64-bit Users</option>
<option value="125" class="fjdpth1" >&nbsp; &nbsp;  Other Community Discussions</option>
<option value="46" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  3rd Party Projects</option>
<option value="249" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Projects</option>
<option value="75" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  BUM - Boot Up Manager</option>
<option value="270" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Full Circle Magazine</option>
<option value="180" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ehcp Control Panel</option>
<option value="76" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Women</option>
<option value="156" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu System Panel</option>
<option value="168" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Christian Edition</option>
<option value="159" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Customization Guide</option>
<option value="251" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntuzilla</option>
<option value="301" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Mythbuntu</option>
<option value="145" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Assistive Technology &amp; Accessibility</option>
<option value="16" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Art &amp; Design</option>
<option value="13" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Community Announcements &amp; News</option>
<option value="93" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Gaming &amp; Leisure</option>
<option value="169" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Education &amp; Science</option>
<option value="100" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Tutorials &amp; Tips</option>
<option value="255" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Outdated Tutorials &amp; Tips</option>
<option value="183" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu LoCo Team Forums</option>
<option value="245" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  United States LoCo Teams</option>
<option value="284" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  US LoCo Teams</option>
<option value="232" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Alabama Team - US</option>
<option value="280" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Alaska Team - US</option>
<option value="209" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Arizona Team - US</option>
<option value="208" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Arkansas Team - US</option>
<option value="188" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  California Team - US</option>
<option value="207" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Colorado Team - US</option>
<option value="248" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Connecticut Team</option>
<option value="225" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Florida Team - US</option>
<option value="210" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Georgia Team - US</option>
<option value="314" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Hawaii Team - US</option>
<option value="247" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Illinois Team</option>
<option value="213" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Indiana - US</option>
<option value="275" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Kansas Team - US</option>
<option value="203" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Kentucky Team - US</option>
<option value="288" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Louisiana Team - US</option>
<option value="292" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Maine Team - US</option>
<option value="224" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Maryland Team - US</option>
<option value="260" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Massachusetts Team</option>
<option value="271" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Michigan Team - US</option>
<option value="282" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Minnesota Team - US</option>
<option value="276" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Mississippi Team - US</option>
<option value="277" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Missouri Team - US</option>
<option value="229" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Montana Team - US</option>
<option value="283" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Nevada Team - US</option>
<option value="289" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  New Hampshire Team - US</option>
<option value="185" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  New Jersey Team - US</option>
<option value="187" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  New Mexico Team - US</option>
<option value="212" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  New York - US</option>
<option value="278" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  North Carolina Team - US</option>
<option value="191" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ohio Team - US</option>
<option value="286" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Oklahoma Team - US</option>
<option value="345" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Oregon Team - US</option>
<option value="228" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Pennsylvania Team - US</option>
<option value="287" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Rhode Island Team - US</option>
<option value="311" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  South Carolina Team - US</option>
<option value="285" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  South Dakota Team - US</option>
<option value="259" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Tennessee Team</option>
<option value="184" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Utah Team - US</option>
<option value="236" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Virginia Team - US</option>
<option value="312" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  West Virginia Team</option>
<option value="263" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Wisconsin Team</option>
<option value="252" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Washington DC Team - US</option>
<option value="190" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Northeastern Team - US</option>
<option value="371" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Nebraska Team - US</option>
<option value="246" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  International LoCo Teams</option>
<option value="186" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Tamil Team - India</option>
<option value="189" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Argentina Team</option>
<option value="349" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Software</option>
<option value="350" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Hardware</option>
<option value="351" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Comunidad</option>
<option value="193" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Kenyan Team - Kenya</option>
<option value="194" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Za Team - South Africa</option>
<option value="195" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ireland Team - Ireland</option>
<option value="196" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Kurdish Team - Kurdistan</option>
<option value="197" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Colombia Team - Colombia</option>
<option value="202" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Andhra Pradesh Team - India</option>
<option value="206" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Catalan Team</option>
<option value="227" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Tunisia Team</option>
<option value="250" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Senegal Team</option>
<option value="258" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Egypt Team</option>
<option value="261" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Sudan Team</option>
<option value="262" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Costa Rica Team</option>
<option value="264" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Saudi Arabia Team</option>
<option value="272" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Lebanon Team</option>
<option value="273" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Paraguay Team</option>
<option value="274" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  United Kingdom Team</option>
<option value="281" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Panama Team</option>
<option value="290" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ecuador Team</option>
<option value="291" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Cameroon Team</option>
<option value="299" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Zimbabwe Team</option>
<option value="300" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Venezuela Team</option>
<option value="303" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Philippine Team</option>
<option value="304" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Georgia Team</option>
<option value="309" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Bangalore Team</option>
<option value="319" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Switzerland Team</option>
<option value="320" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Jordan Team</option>
<option value="347" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Delhi Team</option>
<option value="356" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Galician LoCo Team</option>
<option value="360" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Wales Team</option>
<option value="362" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Chile Team</option>
<option value="363" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Comunidad</option>
<option value="364" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Hardware</option>
<option value="365" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Software</option>
<option value="366" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Instalaci&#65533;n y Actualizaci&#65533;n</option>
<option value="369" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Honduras Team</option>
<option value="372" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Albania Team</option>
<option value="373" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Bolivia Team</option>
<option value="374" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  El Salvador Team</option>
<option value="375" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Quebec Team</option>
<option value="204" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Other Forums &amp; Teams</option>
<option value="348" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Team Forums</option>
<option value="103" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Testimonials &amp; Experiences</option>
<option value="243" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Weekly Newsletter</option>
<option value="310" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Development &amp; Programming</option>
<option value="359" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Karmic Koala Testing and Discussion</option>
<option value="44" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Packaging and Compiling Programs</option>
<option value="201" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Development CD/DVD Image Testing</option>
<option value="306" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Brainstorm</option>
<option value="307" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Dev Link Forum</option>
<option value="39" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Programming Talk</option>
<option value="41" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Repositories &amp; Backports</option>
<option value="47" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Backports</option>
<option value="82" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Bug Reports / Support</option>
<option value="237" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Ubuntu Forum Archives</option>
<option value="346" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Intrepid Ibex Testing and Discussion (Closed)</option>
<option value="352" class="fjdpth4" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Jaunty Jackalope Testing and Discussion (CLOSED)</option>
<option value="308" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Virtualization</option>
<option value="313" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Wine</option>
<option value="175" class="fjdpth1" >&nbsp; &nbsp;  Forum Community Discussions</option>
<option value="11" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  The Community Cafe</option>
<option value="302" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Recurring Discussions</option>
<option value="298" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Community Cafe Games</option>
<option value="38" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Community Market</option>
<option value="48" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Forum Feedback &amp; Help</option>
<option value="181" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Request a LoCo forum</option>
<option value="123" class="fjdpth3" >&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Resolution Center</option>
<option value="357" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  Forum Council Agenda</option>
<option value="122" class="fjdpth2" >&nbsp; &nbsp; &nbsp; &nbsp;  The Fridge Discussions</option>

        </optgroup>
        
    </select><input type="submit" class="button" value="Go"  />
    </form>
</div></td>
</tr>
</table>
<!-- / forum jump -->


<br />

<div class="vbclean_bottom">
<div class="vbclean_bottomfg">


<br />
<div class="smallfont" align="center">All times are GMT -4. The time now is <span class="time">07:58 PM</span>.</div>
<br />


        </div>
    </div>
</div>

<!-- / close content container -->
<!-- /content area table -->

<form action="index.php" method="get">

<table border="0" width="99%" class="vbclean_bottomfg" align="center">
<tr>
    
    
    <td class="tfoot" align="right" width="100%">
        <div class="smallfont">
            <strong>
                
                <a href="http://ubuntuforums.org">Ubuntu Forums</a> -
                
                
                <a href="archive/index.php">Archive</a> -
                
                <a href="#top" onclick="self.scrollTo(0, 0); return false;">Top</a>
            </strong>
        </div>
    </td>
</tr>
</table>

<br />

<div align="center">
    
    <!-- Do not remove this copyright notice -->
    vBulletin  &#65533;2000 - 2009, Jelsoft Enterprises Ltd. Ubuntu Logo, Ubuntu and Canonical &#65533; Canonical Ltd. Tango Icons &#65533; Tango Desktop Project. bilberry
    <!-- Do not remove this copyright notice -->
    

    
    <!-- Do not remove  or your scheduled tasks will cease to function -->
    
    <!-- Do not remove  or your scheduled tasks will cease to function -->

    
    
</div>

</form>




<script type="text/javascript">
<!--
    // Main vBulletin Javascript Initialization
    vBulletin_init();
//-->
</script>
</div>

  <b class="vbclean_bottom">
  <b class="vbclean_bottom5"></b>
  <b class="vbclean_bottom4"></b>
  <b class="vbclean_bottom3"></b>
  <b class="vbclean_bottom2"><b></b></b>
  <b class="vbclean_bottom1"><b></b></b></b>
</div>
<br />
<script type="text/javascript">
var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
</script>
<script type="text/javascript">
try {
var pageTracker = _gat._getTracker("UA-361826-29");
pageTracker._trackPageview();
} catch(err) {}</script>


</body>
</html>
```
That looks like the Ubuntu Forums' menu page HTML code. :)

---

### Post by kerry_s on 2009-09-30
it's okay.
try this:

xmessage:

```

#!/bin/sh
read=`xmessage -fn 9x15 -g -5+10 "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile ~/recording.asf &
 xmessage -fn 9x15 -g -5+10 "Stop Recorder" -buttons Stop;killall mplayer
fi

if [ $read = "Cancel" ]; then
	exit 0
fi


```

i forgot to mention, if you want it the pretty gtk+ we can use "gmessage" instead, but gmessage is not installed in a default system so you would have to install it with apt-get or synaptic. just letting you know.

---

### Post by days_of_ruin on 2009-09-30
Ok, I fixed the script, here it is:
```
#!/usr/bin/env bash 
RES=`zenity --question --text="What do you want to do?" --cancel-label="Stop Recording" --ok-label="Start Recording"` 
case $? in
    0)  
        mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf ;;
    1)  
        killall mplayer;;
    -1) 
        echo "no response";;
esac

```

I tested this and it works. It saves the recording in whatever directory its run from.

---

### Post by community nerd on 2009-09-30
I am very new to programming to. How did you associate bash script with zenity. Like how do you make zenity work with the script.

---

### Post by kerry_s on 2009-09-30
> **days_of_ruin said:**
> Ok, I fixed the script, here it is:
```
#!/usr/bin/env bash 
RES=`zenity --question --text="What do you want to do?" --cancel-label="Stop Recording" --ok-label="Start Recording"` 
case $? in
    0)  
        mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf ;;
    1)  
        killall mplayer;;
    -1) 
        echo "no response";;
esac

```

I tested this and it works. It saves the recording in whatever directory its run from.

that's funny cause i can see the zenity line is wrong & running just that in a term:

---

### Post by kerry_s on 2009-09-30
> **community nerd said:**
> I am very new to programming to. How did you associate bash script with zenity. Like how do you make zenity work with the script.

i don't know how to explain it so you would be able to understand. :lolflag:

---

### Post by days_of_ruin on 2009-09-30
> **kerry_s said:**
> that's funny cause i can see the zenity line is wrong & running just that in a term:

What version of zenity are you running?

---

### Post by kerry_s on 2009-09-30
i think you should install gmessage:
sudo apt-get install gmessage

with gmessage:
```

#!/bin/sh
read=`gmessage -center "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile ~/recording.asf &
 gmessage -center "Stop Recorder" -buttons Stop;killall mplayer
fi

if [ $read = "Cancel" ]; then
	exit 0
fi

```

example of my xmessage converted to gmessage, big difference in looks & speed:

---

### Post by kerry_s on 2009-09-30
> **days_of_ruin said:**
> What version of zenity are you running?

2.22.1-2 on debian lenny.

i don't see "--cancel-label" & "--ok-label" in the man page for my version, the first part is fine "zenity --question --text="What do you want to do?""

hey, i apologize for my wording, not trying to be confrontational. just got out of the shower so i'm a little more awake & i can see that what i put may not have been in a friendly way. again sorry.

---

### Post by NinjaNumberNine on 2009-09-30
> **days_of_ruin said:**
> Ok, I fixed the script, here it is:
```
#!/usr/bin/env bash 
RES=`zenity --question --text="What do you want to do?" --cancel-label="Stop Recording" --ok-label="Start Recording"` 
case $? in
    0)  
        mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf ;;
    1)  
        killall mplayer;;
    -1) 
        echo "no response";;
esac

```I tested this and it works. It saves the recording in whatever directory its run from.
Very nice, but I wish the dialog box would stay up when you clicked the button Start Recording and shut down when you click Stop Recording. Also it would be nice if there was another button to "Play Recorded File." (In that case you would probably want to disable all "dialog shutdown" commands) Another thing is that it does not drop the file in the folder I run the script from, (/home/myusrname/bin) but instead saves it as "/home/myusrname/Documents/recording.asf" for some reason. Yet _another_ "thing" is that it saves the file as .asf, and if you try playing it, you will see the problem right away- you can't rewind or fast forward without it shooting you back to the beginning of the file. *Sigh* if only I could make it transcode to mp3 automatically...

---

### Post by days_of_ruin on 2009-09-30
Does this radio station have a .m3u stream? If it does, that makes it really easy to save it to an mp3 file.

BTW it is not possible with zenity to make the window stay open.
If you really want that you would have to use a real programming language.

---

### Post by kerry_s on 2009-09-30
i agree, you would actually be writing a program, little scripts no problem, a whole program, your on your own. :lolflag:

like i said, you can us multiple scripts to get the same effect.

the download location is determined by the command. so:
mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile **/home/myusrname/Documents/**recording.asf

should get it where you want.

i hope you have the mplayer gui? added it to the script should play when you stop.

```
#!/bin/sh
read=`gmessage -center "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile ~/Documents/recording.asf &
 gmessage -center "Stop Recorder" -buttons Stop;killall mplayer; gmplayer ~/Documents/recording.asf
fi

if [ $read = "Cancel" ]; then
	exit 0
fi
```

---

### Post by NinjaNumberNine on 2009-10-01
> **days_of_ruin said:**
> Does this radio station have a .m3u stream? If it does, that makes it really easy to save it to an mp3 file.

BTW it is not possible with zenity to make the window stay open.
If you really want that you would have to use a real programming language.
That's not entirely good news...:(  No, the stream does not have an .m3u stream. (That I know of, anyway.)
And about the "it's not possible to keep the window open with zenity" thing.... That is rather inconvenient. I don't mind the graphics on Kerry's dialog, that is fine, so I guess I will use it. However, there are several video/audio convertors for Kubuntu. (That's the one I'm using right now.) Don't you think we could somehow add to the script the command-line options for WinFF (that's a command-based convertor I use) to convert the asf file to mp3? Once again, whatever the answer, thanks for all the help, I would still be doing research if you guys had not helped. :)

---

### Post by NinjaNumberNine on 2009-10-01
> **kerry_s said:**
> i agree, you would actually be writing a program, little scripts no problem, a whole program, your on your own. :lolflag:

like i said, you can us multiple scripts to get the same effect.

the download location is determined by the command. so:
mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile **/home/myusrname/Documents/**recording.asf

should get it where you want.

i hope you have the mplayer gui? added it to the script should play when you stop.


EDIT:There could be a button next to "Stop Recording" to "Convert To Mp3" (or it could do it automatically, doesn't matter to me)

```
#!/bin/sh
read=`gmessage -center "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile ~/Documents/recording.asf &
 gmessage -center "Stop Recorder" -buttons Stop;killall mplayer; gmplayer ~/Documents/recording.asf
fi

if [ $read = "Cancel" ]; then
    exit 0
fi
```

Thanks, Kerry. That script does everything I expected to do from post #1. However, if you have some free time, could you or "Days_Of_Ruin" add the converting process to the script? I think[ this link]("http://www.smorgasbord.net/converting-video-in-linux-using-ffmpeg-and-mencoder/") will tell you all you need to know...
The command to actually convert the file to mp3 should go like this: **ffmpeg -i /home/halstan/Documents/recording.asf -f mp3 /home/halstan/Music/KARNHD.mp3 **(I added the username, you can put that in the script, but don't misuse it, please; this is my Dad's computer)


EDIT: I tested that boldened command and it worked great. The file is now an Mp3, and plays like a normal mp3. I am going to get dangerous and try to add it to the script myself, I'll post back here with any progress. Thanks for all the help!

---

### Post by kerry_s on 2009-10-01
alright conversion added.

```

#!/bin/sh
read=`gmessage -center "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile /home/halstan/Music/recording.asf &
 gmessage -center "Stop Recorder" -buttons Stop;killall mplayer;ffmpeg -i /home/halstan/Documents/recording.asf -f mp3 /home/halstan/Music/KARNHD.mp3;gmplayer /home/halstan/Music/KARNHD.mp3
fi

if [ $read = "Cancel" ]; then
    exit 0
fi

```

does the player come up alright at the end? i put gmplayer for that part.

---

### Post by NinjaNumberNine on 2009-10-02
> **kerry_s said:**
> alright conversion added.

```

#!/bin/sh
read=`gmessage -center "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile /home/halstan/Music/recording.asf &
 gmessage -center "Stop Recorder" -buttons Stop;killall mplayer;ffmpeg -i /home/halstan/Documents/recording.asf -f mp3 /home/halstan/Music/KARNHD.mp3;gmplayer /home/halstan/Music/KARNHD.mp3
fi

if [ $read = "Cancel" ]; then
    exit 0
fi

```does the player come up alright at the end? i put gmplayer for that part.
I got bored and "accidentally" got the conversion part in there myself *stares in shock* :shock: ,   this is how mine turned out:
```
#!/bin/sh
read=`gmessage -center "Stream Recorder" -buttons Record,Cancel -print`

if [ $read = "Record" ]; then
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile ~/Documents/recording.asf &
 mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' &
 gmessage -center "Stop Recorder" -buttons Stop;killall mplayer; ffmpeg -i /home/halstan/Documents/recording.asf -f mp3 /home/halstan/Music/KARNHD.mp3; gmplayer /home/halstan/Music/KARNHD.mp3
fi

if [ $read = "Cancel" ]; then
    exit 0
fi
```So pretty much the same. All I added was the part to play the stream as it records, that's more convenient as I will know when to stop it. (i.e. I will not blindly start and stop the recording, cutting radio sentences in two)

BTW Yep, the gmplayer worked great. Just as a question, is there a way to add another pane to the script? I want it to show a box "Where do you want to save this file?" before it starts recording. Is that possible? 

P.S. Just a laugh, but : 
Employer: "For this job I need someone who is responsible."
Applicant: "I'm the one you want. On my last job, every time something when wrong, they said I was responsible." :lolflag:

---

