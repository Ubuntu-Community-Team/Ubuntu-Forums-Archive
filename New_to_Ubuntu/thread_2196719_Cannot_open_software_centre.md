---
title: "Cannot open software centre"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by michaelerdis on 2013-12-31
Morning guys,
I tried to install itunes on my computer, after which I found I could not open the software centre.
If any one can help I would be most greatfull.
The error code shown when opening the pacgae mager is listed below.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Thank you,
Michael.

---

### Post by carl4926 on 2013-12-31
AFAIK iTunes sucks
There is no Linux application of it and running it is done via Wine, and IIRC only an odd version or so will work, and then only limited/poor.

If I were you I'd start planning to dump all your Vendor Lock in stuff and free yourself from the burden.

---

### Post by michaelerdis on 2013-12-31
As being totally new to ubuntu how would I dump as you suggest.
Michael

---

### Post by carl4926 on 2013-12-31
What I mean is you tied yourself in to Apple
I don't have any Apple products on principle. Dump meant, change to a more open device.
Some i devices (ipod iphone etc..) might work ie; managing music on your device, using rhythmbox 
My guess is also that there is no Ubuntu One/Music app for your Apple device either

---

### Post by Elfy on 2013-12-31
can we get this back ontopic and deal with the issue at hand first or they'll not be installing anything - thanks ;)

Open a terminal - paste this command in and post the WHOLE output back so we can check you've only got the one error in it.

```
cat /etc/apt/sources.list.d/playonlinux.list
```

---

### Post by michaelerdis on 2013-12-31
Good Morning Elfy,
```

michael@michael-G60J:~$ cat /etc/apt/sources.list.d/playonlinux.list
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="fr" lang="fr">
<head>
<title>Debian and Ubuntu repository - PlayOnLinux - Run your Windows applications on Linux easily!</title>
    <meta name="keywords" content="pol, linux, wine, steam, world, of, warcraft, guild, wars, jouer, gratuit, ubuntu, debian, mandriva, redhat, jeux, playonlinux, play, gentoo, fedora, suse, opensuse, projet, jedi, knight, adademy, half, life, silkroad, diablo, starcraft, forums, tomb, raider, elder, scroll, oblivion, morrowind, facilement, gratuito, free, jugar, foro, facilmente, easily, simply, videojuegos, games, juegos" />
    <meta name="dc.keywords" content="pol, linux, wine, steam, world, of, warcraft, guild, wars, jouer, gratuit, ubuntu, debian, mandriva, redhat, jeux, playonlinux, play, gentoo, fedora, suse, opensuse, projet, jedi, knight, adademy, half, life, silkroad, diablo, starcraft, forums, tomb, raider, elder, scroll, oblivion, morrowind, facilement, gratuito, free, jugar, foro, facilmente, easily, simply, videojuegos, games, juegos" />
    <meta name="subject" content="Jeux vidéos sous Linux" />
    <meta name="Classification" content="jouer, linux, wine, facilement" />
    <meta name="description" content="PlayOnLinux will allow you to play your favorite games on Linux easily" />
<meta name="author" content="Quentin Pâris" />
<meta name="revisit-after" content="1 day" />
<meta name="identifier-url" content="http://www.playonlinux.com" />
<meta name="publisher" content="Quentin Pâris" />
<meta name="Robots" content="all" />
<meta name="Rating" content="General" />
<meta http-equiv="VW96.OBJECT TYPE" content="Document" />
<meta name="Category" content="Document" />
<meta name="Page-topic" content="Document" />
<meta name="contactState" content="France" />
<meta http-equiv="Content-Language" content="en"/>
<meta http-equiv="Content-type" content="text/html;charset=UTF-8" />
<meta name="location" content="France, FRANCE" />
<meta name="expires" content="never" />
<meta name="date-revision-ddmmyyyy" content="" />
<meta name="Distribution" content="Global" />
<meta name="Audience" content="General" />
<meta name="verify-v1" content="YhCHh8OKlW7y6fu1VovKLmGvw3YFnSwhQLyzV/yhGpM=" />
<meta http-equiv="Content-Script-Type" content="text/javascript" />
<meta http-equiv="Content-Style-Type" content="text/css" />
<link rel="icon" type="image/png" href="http://www.playonlinux.com/images/logos/logo16.png" />
<link rel="image_src" type="image/jpeg" href="http://www.playonlinux.com/images/logos/logo128.png" />
<link href="http://deb.playonlinux.com/css/design.css" rel="stylesheet" type="text/css" />
<link href="http://www.playonlinux.com/css/forums.css" rel="stylesheet" type="text/css" />
<link href="http://www.playonlinux.com/css/jquery.lightbox-0.5.css" rel="stylesheet" type="text/css" />    
<link href="http://www.playonlinux.com/css/nyroModal.css" rel="stylesheet" type="text/css" />    

<link href="http://www.playonlinux.com/en/rss.xml" title="Mon flux RSS" type="application/RSS+XML" rel="alternate" />


<script type="text/javascript">
var url = "http://www.playonlinux.com";
var prefixe = "http://www.playonlinux.com/en";
</script>
<script type="text/javascript" src="http://www.playonlinux.com/js/retina.js"></script>

<script type="text/javascript" src="http://www.playonlinux.com/js/jquery/jquery.js"></script>
<script type="text/javascript" src="http://www.playonlinux.com/js/jquery/jquery.lightbox-0.5.js"></script>
<script type="text/javascript" src="http://www.playonlinux.com/js/jquery/jquery.textarea.js"></script>

<script type="text/javascript" src="http://www.playonlinux.com/js/design.js"></script>

<script type="text/javascript" src="http://www.playonlinux.com/js/nicEdit.js"></script>


<script type="text/javascript">
$(function() {
    $('a.lightbox').lightBox();
});
jQuery(document).ready(function () {

     $("textarea").tabby();

});
</script>

<!-- Syntax Hilighter -->
<!-- Special thank you to [http://alexgorbatchev.com/SyntaxHighlighter/](http://alexgorbatchev.com/SyntaxHighlighter/) --> 
<script type="text/javascript" src="http://www.playonlinux.com/js/highlighter/shCore.js"></script>
<link type="text/css" rel="stylesheet" href="http://www.playonlinux.com/css/highlighter/shCorePOL.css" />
<script type="text/javascript">SyntaxHighlighter.all();</script>

</head>
<body>
<div id="design">
<div id="header">
        <a href="http://www.playonlinux.com/en"><img src="http://www.playonlinux.com/images/design/playonlinux.jpg" alt="PlayOnLinux" /></a>
      <ul id="menuul">
        <li><a href="http://www.playonlinux.com/en">Home</a></li> 
        <li><a href="http://www.playonlinux.com/en/news.html">News</a></li>
        <li><a href="http://www.playonlinux.com/en/download.html">Download</a></li>
    <li><a href="http://www.playonlinux.com/en/documentation.html">Documentation</a></li>
        <li><a href="http://www.playonlinux.com/en/forums.html">Forums</a></li>
        <li><a href="http://www.playonlinux.com/en/bugs.html">Bugs</a></li>
    

    </ul>
</div>
<div id="page">
    <p class='youarehere'>
                    <a href="http://www.playonlinux.com/sv"><img src="http://www.playonlinux.com/images/flags/sv.png" alt="sv" /></a>
                                        <a href="http://www.playonlinux.com/ru"><img src="http://www.playonlinux.com/images/flags/ru.png" alt="ru" /></a>
                                        <a href="http://www.playonlinux.com/pl"><img src="http://www.playonlinux.com/images/flags/pl.png" alt="pl" /></a>
                                        <a href="http://www.playonlinux.com/es"><img src="http://www.playonlinux.com/images/flags/es.png" alt="es" /></a>
                                        <a href="http://www.playonlinux.com/fr"><img src="http://www.playonlinux.com/images/flags/fr.png" alt="fr" /></a>
                    </p>
<div id="contenu">
<h1>PlayOnLinux debian and ubuntu repository</h1>

<p>
<img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_quantal.list'>playonlinux_quantal.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_intrepid.list'>playonlinux_intrepid.list</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='conf'>conf</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='incoming'>incoming</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='db'>db</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_hardy.list'>playonlinux_hardy.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_maverick.list'>playonlinux_maverick.list</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='css'>css</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='pool'>pool</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_jaunty.list'>playonlinux_jaunty.list</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='images'>images</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_natty.list'>playonlinux_natty.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_karmic.list'>playonlinux_karmic.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_squeeze.list'>playonlinux_squeeze.list</a><br /><img src='/.images/dossier.png' style='margin-right:5px' /><a href='dists'>dists</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_etch.list'>playonlinux_etch.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='public.gpg'>public.gpg</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_lucid.list'>playonlinux_lucid.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_wheezy.list'>playonlinux_wheezy.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_precise.list'>playonlinux_precise.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_oneiric.list'>playonlinux_oneiric.list</a><br /><img src='/.images/fichier.png' style='margin-right:5px' /><a href='playonlinux_lenny.list'>playonlinux_lenny.list</a><br />    </p>
    </div>

<div id="menu_droite">
    <h1>Login</h1>
        <form action="http://www.playonlinux.com/membre/login.php" method="post">
    <div class="login_texte">Username : </div><div class="login_contenu"><input type="text" class="champ_petit" name="login"/></div>
    <div class="espace"></div>
    <div class="login_texte">Password : </div><div class="login_contenu"><input type="password" class="champ_petit" name="passwd"/></div>
    <div class="espace"></div>
    <div class="login_texte">Remember: </div><div class="login_contenu"><input type="checkbox" name="auto" value="1" /></div>
    <div class="espace"></div>
    <input type="hidden" name="referer" value="/" />
    <div class="boutton_login"><input type="submit" value="Login" class="boutton" /></div>
    </form>
    <ul class='menu'>
        <li><a href="http://www.playonlinux.com/en/register.html">Register</a></li> 
    </ul>
        
    <p class='online'><b>264</b>  people online</p>

    <h1>Follow us</h1>
    <div id="folw">
    <a href="https://plus.google.com/u/0/105992880311102680198"><img src="http://www.playonlinux.com/images/social2/googleplus.png" alt="Google+" /></a>

    <a href="http://www.playonlinux.com/en/rss.xml"><img src="http://www.playonlinux.com/images/social2/rss.png" alt="RSS" /></a>

    <a href="http://facebook.com/pages/PlayOnLinux/10150094517755063"><img src="http://www.playonlinux.com/images/social2/facebook.png" alt="Facebook" /></a>
    <a href="http://twitter.com/PlayOnLinux"><img src="http://www.playonlinux.com/images/social2/twitter.png" alt="Twitter" /></a>
         
    
        
        
    </div>
    <h1>Menu</h1>
    <ul class="menu">    

    <li><a href="http://www.playonlinux.com/en/supported_apps.html">Supported software</a></li>
    <li><a href="http://www.playonlinux.com/en/team.html">The website team</a></li>
    <li><a href="http://www.playonlinux.com/en/membres.html">Member list</a></li>
    <li><a href="http://www.playonlinux.com/en/donate.html">Donate</a></li>
    
    </ul>



<h1>Ads</h1>
<p id="ads">
<script type="text/javascript"><!--
google_ad_client = "pub-3469449563864685";
/* 160x600, droite */
google_ad_slot = "8995026268";
google_ad_width = 160;
google_ad_height = 600;
//-->
</script>
<script type="text/javascript"
src="http://pagead2.googlesyndication.com/pagead/show_ads.js">
</script>

</p>

<script type="text/javascript"><!--
if(document.getElementsByTagName("iframe").item(0) == null)
{

    document.write("<div style='width:160px; height:600px; padding-top: 280px; margin-left:5px;border:1px solid #666666; color:#FFF; background-color:#666; text-align:center; font-family:Maven Pro,century gothic, arial, helvetica, sans serif;padding-left:5px;padding-right:5px;border-radius:7px;font-size:18px;'>Advertising seems to be blocked by your browser.<br /><br /><span style='font-size:12px'>Please notice that advertising helps us to host the project.<br /><br />If you find these ads intrusive or inappropriate, please contact me.</span><br /><img src='http://www.playonlinux.com/images/abp.png' alt='Adblock Plus' /></div>");
};
--></script>

<h1>Partners</h1>
<p><a href="http://www.jeuxlinux.fr" target="_blank"><img src="http://www.playonlinux.com/images/logo_jeuxlinux.png" alt="Jeux linux"/></a></p>
<p><a href="http://www.linuxpedia.fr" target="_blank"><img src="http://www.playonlinux.com/images/ban-LP.png" alt="Linux-pedia" /></a></p>
<!-- <p><a href="http://www.wine-reviews.net/" target="_blank"><img src="http://www.playonlinux.com/images/winereview.png" alt="Wine-Review" /></a></p> -->

</div>
</div>

</div>
<script type="text/javascript">
var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
</script>
<script type="text/javascript">
try {
var pageTracker = _gat._getTracker("UA-7841956-1");
pageTracker._trackPageview();
} catch(err) {}</script>

<div class="coms"><a href="http://www.playonlinux.com/comments.php">Il n'y a rien à voir ici</a></div>
</body>
</html>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3c.org/TR/1999/REC-html401-19991224/loose.dtd">
<html><head><title>Vodafone Mobile Wi-Fi</title>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type">
<meta content="text/css" http-equiv="Content-Style-Type">
<meta content="no-cache" http-equiv="Pragma">
<meta content="no-cache" http-equiv="Cache-Control">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<link rel="stylesheet" type="text/css" href="/css/main.css"/>
<link rel="shortcut icon" type="image/x-icon" href="/favicon.ico" />
<link rel="Bookmark"  href="/favicon.ico"/>
<script type="text/javascript" src="/lang.js"></script>
<script type="text/javascript" src="/lang/en_new.js"></script>
<script type="text/javascript">
dir_ltr = 'ltr';
dir_left = 'left';
dir_right = 'right';
langIndex = 0;
var langlist = [
[langid_auto, 0],
[langid_ar, 8],
[langid_az, 26],
[langid_bg, 27],
[langid_zh, 2],
[langid_hr, 3],
[langid_cs, 4],
[langid_da, 5],
[langid_nl_nld, 7],
[langid_en, 1],
[langid_ee, 28],
[langid_fi, 9],
[langid_fr_fra, 11],
[langid_de, 12],
[langid_el, 13],
[langid_hu, 14],
[langid_it, 15],
[langid_lv, 16],
[langid_lt, 17],
[langid_no, 18],
[langid_pt, 19],
[langid_ro, 20],
[langid_ru, 21],
[langid_sl, 22],
[langid_es, 23],
[langid_se, 24],
[langid_tr, 25] 
];</script>
<script language="javascript">
if( typeof(dont_timeout)=='undefined' || dont_timeout==undefined || !dont_timeout )
setTimeout('document.location.href="logout.cgi";',300000);
iPageErr = 0;
OPCO_DN_GPRS = 'GPRS';
OPCO_DN_G3 = '3G';
OPCO_DN_HSDPA = 'HSDPA';
OPCO_DN_EDGE = 'EDGE';
OPCO_DN_WebSessionsName = 'WebSessions';
OPCO_DN_HSUPA = 'HSUPA';
OPCO_DN_HSPAPLUS = 'HSPA+';
OPCO_DN_LAN = 'LAN';
OPCO_DN_WLAN = 'WLAN';
OPCO_DN_WWAN = 'WWAN';
OPCO_DN_GPRS = 'GPRS';
OPCO_DN_G3 = '3G';
OPCO_DN_HSDPA = 'HSDPA';
OPCO_DN_EDGE = 'EDGE';
OPCO_DN_WebSessionsName = 'WebSessions';
OPCO_DN_HSUPA = 'HSUPA';
OPCO_DN_HSPAPLUS = '3G+';
OPCO_DN_LAN = 'LAN';
OPCO_DN_WLAN = 'WLAN';
OPCO_DN_WWAN = 'WWAN';
</script>

<script type="text/javascript" src="/html/js/main.js"></script>
<script type="text/javascript" src="/html/js/async_class.js"></script>
<script type="text/javascript">
var MACRO_INVALID_DATA = -11111;
var MACRO_PIN_REQ = 260;
var MACRO_PUK_REQ = 261;
var MACRO_NO_SIM_CARD = 255;
var MACRO_PPP_CONNECTED = 1;
var sysinfo = [2,3,0,5,1,0,4];
var g_pin_state_and_remain_times = [257,-1];
var g_sim_pin_state = g_pin_state_and_remain_times[0];
var g_pin_remain_times = g_pin_state_and_remain_times[1];
var dhcp_settings = [-1062731775,-256,1,-1062731676,-1062731576,86400];
var gateway_domain = "VodafoneMobile.WiFi";
var ppp_con_state = 1;
var getaway_address;
gateway_domain = gateway_domain.toLowerCase();

function inet_ntoa(n)
{
    var a;

    a = (n >> 24) & 255;
    a += "."
    a += (n >> 16) & 255;
    a += "."
    a += (n >> 8) & 255;
    a += "."
    a += n & 255;

    return a;
}

function change_url()
{
    if( dhcp_settings == MACRO_INVALID_DATA )
    {
        getaway_address = "192.168.0.1";
    }
    else
    {
        getaway_address = inet_ntoa(dhcp_settings[0]);
    }
    
    var url1 = "http://"+getaway_address+"/"+"login.htm";
    var url2 = "http://"+gateway_domain+"/"+"login.htm";
    var url3 = "http://"+gateway_domain+"/";
    var url4 = "http://"+getaway_address+"/";
    var url = top.window.location.toString();
    if( url == url1 || url == url2 || url == url3 || url == url4 )
    {
        return;
    }
    else
    {
        if( ppp_con_state == MACRO_PPP_CONNECTED )
        {
            top.location.replace( "http://"+gateway_domain+"/"+"redir_.htm");
        }
        else
        {
            top.location.replace( "http://"+gateway_domain+"/"+"redir.htm");
        }
    }
}
change_url();

function change_for_pin()
{
    if( dhcp_settings == MACRO_INVALID_DATA )
    {
        getaway_address = "192.168.0.1";
    }
    else
    {
        getaway_address = inet_ntoa(dhcp_settings[0]);
    }
    
    if(g_sim_pin_state == MACRO_PIN_REQ || g_sim_pin_state == MACRO_PUK_REQ 
        || g_sim_pin_state == MACRO_NO_SIM_CARD || sysinfo[4] == MACRO_NO_SIM_CARD)
    {
        top.location.replace( "http://"+gateway_domain+"/"+"redir.htm");
    }
}
change_for_pin();

function init()
{
    var cf = self.document.forms[0];
    cf.elements["AdPassword"].focus();
    if (window.iPageErr)
        alert(sPageErr);
}
</script>
</head>
<body id="top" onload="init(); " lang="en">
<div id="allcontent2">
<script type="text/javascript">
    genloginheader( langlist, '', './' );
</script>
    <div class="intro">
        <p class="intro">
        <script type="text/javascript">dw(login_welcome_t2)</script></span></p>
        <p>
        <table width=540>
        <tr><td>
           <script type="text/javascript">dw(login_desc_t1)</script>
           <br><br><script type="text/javascript">dw(login_desc_t2)</script>
        </td></tr>
        </table>
        </p>
    </div>
</div>
</body>
</html>
michael@michael-G60J:~$ 

```
Hope you can hep,
Michael

---

### Post by carl4926 on 2013-12-31
Just FYI
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by Elfy on 2013-12-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Ok - so yea - that is rather broken.

```
sudo rm /etc/apt/sources.list.d/playonlinux.list && sudo apt-get update
```

That will remove the bad file and update apt again.

At that point you'll be able to use software centre again.

If you want to use the playonlinux repos then you need to redo the installing of it again.

Where did you get the information from to add it last time - and what version Ubuntu are you using? 

As far as your itunes issue goes - some manage for a short while, others don't. I never got into that situation, much like carl4296. Can't help you with that.

This is the result of an itunes search on *buntu specific sources - [http://bit.ly/1hbpy7D](http://bit.ly/1hbpy7D)

---

### Post by Elfy on 2013-12-31
> **carl4926 said:**
> Just FYI
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

ta carl4926. 

Horrid stuff imo :)

---

