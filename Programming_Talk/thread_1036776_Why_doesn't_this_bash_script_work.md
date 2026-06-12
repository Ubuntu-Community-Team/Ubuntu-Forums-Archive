---
title: "Why doesn't this bash script work?"
date: 2009-01-11
forum: Programming Talk
---

### Post by Nevon on 2009-01-11
```
#!/bin/sh
#Ungdomar.se script
#
#This script returns the number of unread PMs, blog comments, guestbook entries, etc. from ungdomar.se
#-------------------------------------------------

#Write your username and password here
MY_USERNAME=username
MY_PASSWORD=password

#-------------------------------------------------
LOGIN_DATA="action=login&login_nick=$MY_USERNAME&login_pwd=$MY_PASSWORD"

#Downloads the index page
cd /tmp/um
wget --quiet --save-cookies --save-session-cookies --post-data $LOGIN_DATA --user-agent 'Firefox' -O um.htm http://ungdomar.se/index.php

#Extracts the number of forum comments
FORUM_NUMBER=`cat um.htm | LANG=se_SE.iso88591 sed -n 's/.*forumkommentar.*count..\([0-9]*\).*/\1/p'`
#Extract the number of guestbook posts
GUESTBOOK_NUMBER=`cat um.htm | LANG=de_SE.iso88591 sed -n 's/.*g.stbok.*count..\([0-9]*\).*/\1/p'`
#Extract the number of PM:s
PM_NUMBER=`cat um.htm | LANG=se_SE.iso88591 sed -n 's/.*ol.st.*pm.*count..\([0-9]*\).*/\1/p'`
#Extract the number of blog comments
BLOGG_NUMBER=`cat um.htm | LANG=se_SE.iso88591 sed -n 's/.*bloggkommentar.*count..\([0-9]*\).*/\1/p'`
#Extract the number of image comments
IMAGE_NUMBER=`cat um.htm | LANG=se_SE.iso88591 sed -n 's/.*albumkommentar.*count..\([0-9]*\).*/\1/p'`

#Sets the different variables to 0 if no unread messages were found
if [ -z "$PM_NUMBER" ]; then
	PM_NUMBER=0
fi
if [ -z "$BLOGG_NUMBER" ]; then
	BLOGG_NUMBER=0
fi
if [ -z "$GUESTBOOK_NUMBER" ]; then
	GUESTBOOK_NUMBER=0
fi
if [ -z "$FORUM_NUMBER" ]; then
	FORUM_NUMBER=0
fi
if [ -z "$IMAGE_NUMBER" ]; then
	IMAGE_NUMBER=0
fi

echo "PM: $PM_NUMBER | Bloggkommentarer: $BLOGG_NUMBER | Gästboksinlägg: $GUESTBOOK_NUMBER | Forumciteringar: $FORUM_NUMBER | Bildkommentarer: $IMAGE_NUMBER"

#Removes the downloaded file
rm um.htm
```

Why doesn't this work? Wget downloads the index-file after logging in, and if you, for example, have any unread PMs you'd get this message on the index page:
```
<a href="pm.php"><img src="/gfx/pm_unread.png" alt="" title="Du har 1 oläst pm." width="17" height="12"></a>
```
The script finds this with the regular expression 's/.*ol.st.*pm.*count..\([0-9]*\).*/\1/p' and returns the number. However, if you don't have any unread PMs, it won't return anything at all. That's why I have the conditional statements that sets the variables to 0 if they are empty. 
However, for some reason the script always returns 0, even if you do have unread messages.

I've never really written any bash scripts before, so be gentle. If you know a better way to fix the issue with empty variables without using 5 different conditional statements, please say so.

---

### Post by Nevon on 2009-01-11
I had to urlencode both my username and password. Now if I could only get some neat way of doing that directly in the script...?

---

### Post by eightmillion on 2009-01-11
> **Nevon said:**
> I had to urlencode both my username and password. Now if I could only get some neat way of doing that directly in the script...?

You could always use a bit of python. Something like this:

```
#-------------------------------------------------

#Write your username and password here
MY_USERNAME=username
MY_PASSWORD=password

#------------------------------------------------
MY_USERNAME=$(echo $MY_USERNAME | python -c 'import urllib,sys;sys.stdout.write(urllib.quote(sys.stdin.read()))')
MY_PASSWORD=$(echo $MY_PASSWORD | python -c 'import urllib,sys;sys.stdout.write(urllib.quote(sys.stdin.read()))')

LOGIN_DATA="action=login&login_nick=$MY_USERNAME&login_pwd=$MY_PASSWORD"

```

---

### Post by Nevon on 2009-01-11
> **eightmillion said:**
> You could always use a bit of python. Something like this:

```
#-------------------------------------------------

#Write your username and password here
MY_USERNAME=username
MY_PASSWORD=password

#------------------------------------------------
MY_USERNAME=$(echo $MY_USERNAME | python -c 'import urllib,sys;sys.stdout.write(urllib.quote(sys.stdin.read()))')
MY_PASSWORD=$(echo $MY_PASSWORD | python -c 'import urllib,sys;sys.stdout.write(urllib.quote(sys.stdin.read()))')

LOGIN_DATA="action=login&login_nick=$MY_USERNAME&login_pwd=$MY_PASSWORD"

```

That gives the output %C3%85tta%0A from my username (Åtta). I need it to be exactly %C5tta, which is what PHP gives.

---

### Post by eightmillion on 2009-01-11
> **Nevon said:**
> That gives the output %C3%85tta%0A from my username (Åtta). I need it to be exactly %C5tta, which is what PHP gives.

I get the same thing as python with both PHP and ruby.

```
$ echo "Åtta" | php -r "print urlencode(trim(fgets(STDIN)));"
%C3%85tta
```

```
$ echo 'Åtta' | ruby -e 'require "cgi";print CGI.escape(STDIN.read.chomp)'
%C3%85tta

```

I don't know what the problem is.

---

### Post by SeanHodges on 2009-01-12
> **eightmillion said:**
> I get the same thing as python with both PHP and ruby.

```
$ echo "Åtta" | php -r "print urlencode(trim(fgets(STDIN)));"
%C3%85tta
```

```
$ echo 'Åtta' | ruby -e 'require "cgi";print CGI.escape(STDIN.read.chomp)'
%C3%85tta
```

I don't know what the problem is.

I believe the character encoding returned by Nevon's Web server is not UTF-8:

```
$ echo "Åtta" | php -r "print urlencode(trim(utf8_decode(fgets(STDIN))));"
%C5tta
```

...and in Ruby:

```
echo 'Åtta' | ruby -e 'require "cgi";require "iconv";ic = Iconv.new("ISO-8859-1", "UTF-8");print CGI.escape(ic.iconv(STDIN.read.chomp))'
%C5tta
```

---

### Post by Nevon on 2009-01-12
> **SeanHodges said:**
> I believe the character encoding returned by Nevon's Web server is not UTF-8:

```
$ echo "Åtta" | php -r "print urlencode(trim(utf8_decode(fgets(STDIN))));"
%C5tta
```

...and in Ruby:

```
echo 'Åtta' | ruby -e 'require "cgi";require "iconv";ic = Iconv.new("ISO-8859-1", "UTF-8");print CGI.escape(ic.iconv(STDIN.read.chomp))'
%C5tta
```

That's right. It's ISO-8859-1, not UTF-8. Sorry for not mentioning that. Your solution works fine, however, that requires php or ruby to be installed on the computer that runs the script. Since that's not typically installed by default, that kind of defeats the purpose of doing the urlencoding directly in the script. If the user is smart enough to install php, he or she can most likely urlencode their login information by themselves and then post it in the script. 

Is there any possible way to do this directly in bash?

---

### Post by guilherme08 on 2009-01-12
> The script finds this with the regular expression [LEFT]'s/.*ol.st.*pm.*count..\([0-9]*\).*/\1/p'[/LEFT] and returns the number.
It's been a long time since I last used sed, but it seems to me that this regexp won't match the pm count, since the word "count" is not present in the index page and the number you want to extract comes before, not after, the expression ol.st.*pm.
That's why sed only returns an empty variable which is then set to zero in your conditional statements.
You could try something like this:
```

sed -n 's/.*Du har \([0-9][0-9]*\).*/\1/p'

```
It substitutes everything from the beginning of the expression up to the number it finds after "Du har", which is at least one digit long, and everything after, for that number.
If you want to handle spaces between "Du", "har", and the number, you can use [[:space:]]*.
And as for the conditional statements, another way to set the variables to 0 is to use "${var:=0}" instead of "$var". This will return $var if the variable is not empty, or assign the value 0 to it if it is.

---

### Post by Nevon on 2009-01-12
> **guilherme08 said:**
> It's been a long time since I last used sed, but it seems to me that this regexp won't match the pm count, since the word "count" is not present in the index page and the number you want to extract comes before, not after, the expression ol.st.*pm.
That's why sed only returns an empty variable which is then set to zero in your conditional statements.
You could try something like this:
```

sed -n 's/.*Du har \([0-9][0-9]*\).*/\1/p'

```
It substitutes everything from the beginning of the expression up to the number it finds after "Du har", which is at least one digit long, and everything after, for that number.
If you want to handle spaces between "Du", "har", and the number, you can use [[:space:]]*.
I'm trying to test it at the moment, but I need people to send me PMs (not PMS) before I can test it, as I can't send them to myself. But if you're right and it doesn't function properly, wouldn't it be the same for blog comments, image comments etc. also? As they are displayed using pretty much the same syntax? That would seem odd, as I was quoted two times this morning, and the script displayed that properly. Anyway, I'll test your version and see what happens.

Okay, now I've got multiple PMs, and it seems to be working fine just the way it is. Also, with your version, what would happen if it said "du har" somewhere in the forum? Plus, if I have unread PMs AND unread guestbook entries (both begin with "Du har"), what would happen?

> **guilherme08 said:**
> And as for the conditional statements, another way to set the variables to 0 is to use "${var:=0}" instead of "$var". This will return $var if the variable is not empty, or assign the value 0 to it if it is.
Ah, thank you! That looks much better.

---

### Post by guilherme08 on 2009-01-12
> But if you're right and it doesn't function properly, wouldn't it be the same for blog comments, image comments etc. also? As they are displayed using pretty much the same syntax?

Yes, it should work in those cases too. All I did was copy the the expression you provided in the first post and extract the last number that appears from it (that matches the regexp), so it should work with any similar expression with a number preceded by "Du har".

> Also, with your version, what would happen if it said "du har" somewhere in the forum? Plus, if I have unread PMs AND unread guestbook entries (both begin with "Du har"), what would happen?

My version extracts the last instance of a number preceded by "Du har", since .* matches anything that comes before it (including other instances):

```

echo '<a href="pm.php"><img src="/gfx/pm_unread.png" alt="" title="Du har 1 oläst pm." width="17" height="12"></a> **Du har 3**' | sed -n 's/.*Du har \([0-9][0-9]*\).*/\1/p'
3

```

I didn't think that would be a problem because I assumed sed would only have to deal with the expression you provided, not the whole .htm file (I should have read your script more carefully)
Of course you can filter the expression you want, for example by replacing Du har \([0-9][0-9]*\).* with s!<a href="pm.php">.*title="Du har \([0-9][0-9]*\)[^<]*</a>.*!\1!p' (that would match the last instance of "Du har" plus a number that is enclosed within <a href="pm.php" and </a>), but if the expression you provided is in a single line, maybe the easiest solution would be to either preceed the substitute command with /"pm.php"/ or to grep it out of the file (by matching "pm.php") and then use your preferred sed regexp to extract the number.

---

### Post by Nevon on 2009-01-12
> **guilherme08 said:**
> Yes, it should work in those cases too. All I did was copy the the expression you provided in the first post and extract the last number that appears from it (that matches the regexp), so it should work with any similar expression with a number preceded by "Du har".



My version extracts the last instance of a number preceded by "Du har", since .* matches anything that comes before it (including other instances):

```

echo '<a href="pm.php"><img src="/gfx/pm_unread.png" alt="" title="Du har 1 oläst pm." width="17" height="12"></a> **Du har 3**' | sed -n 's/.*Du har \([0-9][0-9]*\).*/\1/p'
3

```I didn't think that would be a problem because I assumed sed would only have to deal with the expression you provided, not the whole .htm file (I should have read your script more carefully)
Of course you can filter the expression you want, for example by replacing Du har \([0-9][0-9]*\).* with s!<a href="pm.php">.*title="Du har \([0-9][0-9]*\)[^<]*</a>.*!\1!p' (that would match the last instance of "Du har" plus a number that is enclosed within <a href="pm.php" and </a>), but if the expression you provided is in a single line, maybe the easiest solution would be to either preceed the substitute command with /"pm.php"/ or to grep it out of the file (by matching "pm.php") and then use your preferred sed regexp to extract the number.

It kind of feels like we're trying to fix something that isn't broken. I myself don't understand regular expressions at all. That part was written by another person. However, the current regexp seems to be working just fine. 

This is the full source of the downloaded page. The interesting bits are in the top nav-part. Currently I have 5 unread quotations, 1 blog comment, 1 guestbook entry, and one image comment, all in that order.
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" >
<html>
<head>
<title>Ungdomar.se Forumlista</title>
<meta http-equiv="content-type" content="text/html; charset=windows-1252">
<meta http-equiv="content-language" content="sv">
<link rel="stylesheet" rev="stylesheet" href="/gfx/1/style.css" type="text/css">
<link rel="alternate" href="http://ungdomar.se/rss.php?type=text" type="application/rss+xml" title="Ungdomar.se - Texter">
<link rel="alternate" href="http://ungdomar.se/rss.php?type=forum" type="application/rss+xml" title="Ungdomar.se - Trådar i forumet">
<link rel="alternate" href="http://ungdomar.se/rss.php?type=blogg" type="application/rss+xml" title="Ungdomar.se - Bloggar">
<script type="text/javascript" language="JavaScript" src="/js/global.js"></script>
<script type="text/javascript" language="JavaScript" src="/js/jquery-1.2.1.js"></script>
<script type="text/javascript" language="JavaScript" src="/js/header_search.js"></script><!-- OAS SETUP begin -->

    <SCRIPT type="text/javascript">
    <!--
    //configuration
    OAS_url ='http://oas.minjakt.se/RealMedia/ads/';
    OAS_listpos = 'Top,Right1,Right2,Right3,Right4,Right5,Right6,Right7,Right8,Right9';
    OAS_query = '?';OAS_sitepage = 'www.ungdomar.se/forum';//end of configuration
    OAS_version = 10;
    OAS_rn = '001234567890'; OAS_rns = '1234567890';
    OAS_rn = new String (Math.random()); OAS_rns = OAS_rn.substring (2, 11);
    function OAS_NORMAL(pos) {
    document.write('<A HREF="' + OAS_url + 'click_nx.ads/' + OAS_sitepage + '/1' + OAS_rns + '@' + OAS_listpos + '!' + pos + OAS_query + '" TARGET=_top>');
    document.write('<IMG SRC="' + OAS_url + 'adstream_nx.ads/' + OAS_sitepage + '/1' + OAS_rns + '@' + OAS_listpos + '!' + pos + OAS_query + '" BORDER=0 ALT="Click!"></A>');
    }
    //-->
    </SCRIPT>
    <SCRIPT type="text/javascript">
    <!--
    OAS_version = 11;
    if (navigator.userAgent.indexOf('Mozilla/3') != -1)
    OAS_version = 10;
    if (OAS_version >= 11)
    document.write('<SC'+'RIPT LANGUAGE=JavaScript1.1 SRC="' + OAS_url + 'adstream_mjx.ads/' + OAS_sitepage + '/1' + OAS_rns + '@' + OAS_listpos + OAS_query + '"><\/SCRIPT>');
    //-->
    </SCRIPT><SCRIPT type="text/javascript">
     <!--
     document.write('');
    function OAS_AD(pos) {
    if (OAS_version >= 11 && typeof(OAS_RICH)!='undefined')
      OAS_RICH(pos);
    else
      OAS_NORMAL(pos);
    }
    //-->
    </SCRIPT>
    <!-- OAS SETUP end --></head>
<body>
<a name="top"></a>
<div align="center"><div><table width="1000" border=0 cellspacing=0 cellpadding=0 class="page_frame_color"><tr><td align="center" style="padding:5px 5px 5px 5px;"><div style="margin-bottom:5px;"><SCRIPT type="text/javascript">
  <!--
  OAS_AD('Top');
  //-->
  </SCRIPT></div></td></tr></table></div><table width="1000" border=0 cellspacing=0 cellpadding=0 style="margin-top:5px;"><tr><td><div class="hotlink"><span class="hotlink_desc"><b>Just nu: </b></span><a href="http://ungdomar.se/forum.php?thread_id=248032"><b>VARNING: Fejklänkar härjar på sajten.</b></a>&nbsp;+&nbsp;<a href="http://ungdomar.se/forum.php?thread_id=247787"><b>Tipsa om världens snyggaste fotbollsmål</b></a></div></td><td align="right"><div class="hotlink"><span class="hotlink_desc"><b>Visade F&amp;S: </b></span><a href="qa_nav.php"><b>17,456 miljoner</b></a></div></td></td></tr></table>

<!-- Top nav -->
<table width="1000" border=0 cellspacing=0 cellpadding=0 class="page_frame_color" style="background-image:url(/gfx/1/top_image_08.jpg); background-repeat:no-repeat;">
<tr>
    <td width="730" valign="top">
    <div style="width:420px;">
    <a href="/"><img src="/gfx/1x1.gif" width=420 height=79 border=0></a>
        </div>  
    </td>
    <td width="250" valign="top" class="page_user_frame" style="padding:10px 10px 0px 10px;"><table width="250" border="0" cellpadding="0" cellspacing="0" style="padding-bottom:4px;"><tr><td width="70" valign="top"><img src="/images/48/35/ava_162005.jpg" width=60 height=60></td><td width="180" valign="top"><div class="page_login_name" style="width:180px;">Åtta</div><div class="page_login_meny" style="width:180px; height:10px;"><table cellspacing="0" cellpadding="0"><tr>
        <td><a href="pm.php"><img src="/gfx/pm_unread.png" width="17" height="12" alt="" title="Du har 5 olästa pm." /></a></td>

        <td style="padding-left: 11px;"><a href="blogg_latest.php"><img src="/gfx/blogg_comment_unread.png" width="16" height="14" alt="" title="Du har 1 ny bloggkommentar" /></a></td>
        <td style="padding-left: 11px;"><a href="user_guestbook.php"><img src="/gfx/guestbook_comment_unread.png" width="16" height="14" alt="" title="Du har 1 ny gästbokskommentar" /></a></td>
        
        <td style="padding-left: 11px;"><a href="user_images.php?user_id=162005&func=display_new_comments"><img src="/gfx/folder_comment_unread.png" width="17" height="12" alt="" title="Du har 1 ny albumkommentar" /></a></td>
        
        <td style="padding-left: 11px;" rowspan="2"><img src="/gfx/menu_separator.gif" alt="" /></td>
        </tr><tr>
        <td align="center"><a class="page_login_text" href="pm.php" title="Du har 5 olästa pm."><span class="count">5</span></td>
        <td style="padding-left: 11px;" align="center"><a class="page_login_text" href="blogg_latest.php" title="Du har 1 ny bloggkommentar"><span class="count">1</span></td>
        <td style="padding-left: 11px;" align="center"><a class="page_login_text" href="user_guestbook.php" title="Du har 1 ny gästbokskommentar"><span class="count">1</span></td>

        
        <td style="padding-left: 11px;" align="center"><a class="page_login_text" href="user_images.php?user_id=162005&func=display_new_comments" title="Du har 1 ny albumkommentar"><span class="count">1</span></td>
        
        </tr></table></div></td></tr></table><div class="page_user_dots" style="width:250px;"><img src="/gfx/1x1.gif" width=1 height=3></div><table width="250" class="page_login_meny" border="0" cellspacing="0" cellpadding="0"><tr><td><a href="online.php">499 besökare</a>&nbsp;|</td><td align="right"><a href="user_info.php?user_id=162005">Min sida</a>&nbsp;|&nbsp;<a href="logout.php?action_code=34b9f89a63ff01a8dce21a85700713f3">Logga ut</a></td></tr></table></td>
</tr>
<tr>
<td height="33" colspan="2">
<table width="1000" border=0 cellspacing=0 cellpadding=0>
    <tr>
        <td class="menu_unsel_bg">&nbsp;</td><td class="menu_unsel_bg" valign="bottom"><a href="/"><img src="/gfx/1/menu/index.gif" width=32 height=28 border=0 alt="Hem" onMouseOver="img_over(this, '/gfx/1/menu/index_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/text.php"><img src="/gfx/1/menu/texts.gif" width=51 height=28 border=0 alt="Texter" onMouseOver="img_over(this, '/gfx/1/menu/texts_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/qa_front.php"><img src="/gfx/1/menu/qa.gif" width=99 height=28 border=0 alt="Frågor &amp; Svar" onMouseOver="img_over(this, '/gfx/1/menu/qa_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/folder_index.php"><img src="/gfx/1/menu/folder.gif" width=75 height=28 border=0 alt="Fotoalbum" onMouseOver="img_over(this, '/gfx/1/menu/folder_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=5><img src="/gfx/1/menu_tab_1.png" width=5 height=33></td><td class="menu_tab_bg" valign="bottom"><a href="/forum.php"><img src="/gfx/1/menu/forum_while.gif" width=49 height=28 border=0 alt="Forum"></a></td><td width=5><img src="/gfx/1/menu_tab_3.png" width=5 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/blogg.php"><img src="/gfx/1/menu/blogg.gif" width=61 height=28 border=0 alt="Bloggar" onMouseOver="img_over(this, '/gfx/1/menu/blogg_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/webb_tv_latest.php?prod=1"><img src="/gfx/1/menu/webtv.gif" width=62 height=28 border=0 alt="Webb-TV" onMouseOver="img_over(this, '/gfx/1/menu/webtv_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/chat.php"><img src="/gfx/1/menu/chat.gif" width=42 height=28 border=0 alt="Chat" onMouseOver="img_over(this, '/gfx/1/menu/chat_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/jourhavande_kompis.php"><img src="/gfx/1/menu/jk.gif" width=144 height=28 border=0 alt="Jourhavande Kompis" onMouseOver="img_over(this, '/gfx/1/menu/jk_hover.gif');" onMouseOut="img_out(this);"></a></td><td width=1><img src="/gfx/1/menu_separator.gif" width=1 height=33></td><td class="menu_unsel_bg" valign="bottom"><a href="/about_us.php"><img src="/gfx/1/menu/about.gif" width=52 height=28 border=0 alt="Information" onMouseOver="img_over(this, '/gfx/1/menu/about_hover.gif');" onMouseOut="img_out(this);"></a></td>        <td width="99%" class="menu_unsel_bg">&nbsp;</td>

    </tr>
</table>
</td>
</tr>
</table>

<!-- Sub menu -->
<table width="1000" class="menulink_bg" border=0 cellspacing=0 cellpadding=0><tr>
<td style="padding:8px 0px 8px 10px;"><a class="menulink_active" href="/forum.php">Forum</a>&nbsp;+&nbsp;<a class="menulink" href="/forum.php?view=1">Senaste</a>&nbsp;+&nbsp;<a class="menulink" href="/forum_search.php">Sök</a>&nbsp;+&nbsp;<a class="menulink" href="/forum_add.php">Ny diskussion</a>&nbsp;+&nbsp;<a class="menulink" href="/forum.php?category_id=-1">Favoritforum</a>&nbsp;+&nbsp;<a class="menulink" href="/forum_favorites.php">Bevakade trådar</a>&nbsp;+&nbsp;<a class="menulink" href="/forum_display.php">Visningsläge</a>  </td>

  <td width="200" align="right" style="padding-right:8px;">
      <table border="0" cellpadding="0" cellspacing="0">
        <tr>
        <td><button type="button" class="button_tip" onclick="javascript:vh('tipDiv');">Tipsa</button></td><td width="5">&nbsp;</td>
        <td width="1" valign="middle"><img src="/gfx/header_search_edge.gif" width="1" height="16"></td>
        <td valign="bottom">
        <div style="position:relative; top:0px; left:0px;">
        <form name="header_search" action="forum_search.php" onsubmit="javascript:header_perform_search('forum_search.php');" method="get">

        <input type="text" id="header_sq" name="sq" class="header_search_text" value="Sök på sajten..." onkeyup="header_search_change('forum');" onblur="javascript:if(this.value=='')this.value = 'Sök på sajten...';"  onfocus="javascript:if(this.value=='Sök på sajten...')this.value = '';" style="width:120px;">
        </form>
        <div id="header_search_sites" style="display:none; position:absolute; bottom:25px; right:-2px; z-index:1; color:#ffffff; font-size:9px; background-color:#545050; width:300px;">
        </div>
        </div>
        </td>
        <td width="1" valign="middle"><img src="/gfx/header_search_edge.gif" width="1" height="16"></td>
        </tr>
        </table>

    </td>
</tr></table><!-- Page section -->
<table width="1000" border=0 cellspacing=0 cellpadding=0><tr>
  <td width="740" valign="top"><!-- Data pane -->
        <table width="735" border=0 cellspacing=0 cellpadding=0 style="margin:5px 5px 0px 0px;">
      <tr><td bgcolor="#ffffff" style="padding:15px;"><script type="text/javascript" language="JavaScript" src="/js/forum.js"></script><script type="text/javascript" language="JavaScript" src="/js/textedit.js"></script><table width="100%" border="0" cellpadding="0" cellspacing="0" style="background-image:url(/gfx/paneheader/pane_bg.gif);"><tr><td width="4" height="32" valign="top"><img src="/gfx/paneheader/pane_left.gif" width="4" height="4"></td><td align="left" valign="middle" class="pane_header_text" style="padding-left:5px;">Diskussionsforum</td><td align="right" valign="middle" class="pane_header_text" style="padding-right:6px;"><select id="select_view" style="font-size:11px;" onChange="javascript:window.location='forum.php'+this.options[this.selectedIndex].value;"><option value="">Kategoriserat</option><option value="?view=1">Senast uppdaterade trådar</option><option value="?view=2">Senast skapade trådar</option><option value="?view=3">Olästa citerade trådar</option><option value="?view=4">Alla skrivna/citerade trådar</option></select></td><td width="4" valign="top"><img src="/gfx/paneheader/pane_right.gif" width="4" height="4"></td></tr></table><div class="forum_forum_navigation"><a class="forum_cat_cat" href="forum.php">Forum</a></div><table width="100%" border="0" cellspacing="0" cellpadding="0"><tr class="forum_cat_tbh"><td width="32" style="padding-left:8px;">Nya</td><td width="410">Forum</td><td width="63" align="center">Trådar</td><td width="5">&nbsp;</td><td width="63" align="center">Svar</td><td width="180" style="padding-left:15px;">Ändrad</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=2&view=1">Ungdomar.se</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Nyheter och information om Ungdomar.se.</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=2">Nyheter</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=201758">Chatten buggfixad!</a> <a href="forum.php?thread_id=201758&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">18</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">2221</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: lör 10 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=70313">kebu12</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=37">Sajtinformation</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248032">VARNING: Fejklänkar härjar på sajten.</a> <a href="forum.php?thread_id=248032&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">28</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1986</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 13:24</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=160268">sweptaway</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=62">Önskemål och synpunkter på Ungdomar.se</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248210">Chatten...</a> <a href="forum.php?thread_id=248210&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1762</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">40117</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:36</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=164450">DoktorMaJk</a>&nbsp;</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=7&view=1">Forum AKTUELLT</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Fria forum för diskussioner om aktuellt händelser och nyheter.</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=110">Nu är det jul igen</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=246165">&quot;God jul&quot;-hälsningar</a> <a href="forum.php?thread_id=246165&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">104</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">3806</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: lör 10 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=115118">SilentScream</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=108">Idol 2008</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248467">Loulou - Orsaken till Världshungern?</a> <a href="forum.php?thread_id=248467&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">86</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">3017</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 07:36</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=162005">Åtta</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=107">Presidentvalet i USA</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=241235">Barack Obama vann USAs presidentval 2008!</a> <a href="forum.php?thread_id=241235&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">32</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1267</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: lör 10 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=165904">B3ll4</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=80">Övriga aktuella nyheter och händelser</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248507">wojdat.blogg.se</a> <a href="forum.php?thread_id=248507&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1003</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">58193</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:41</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=156143">Hejjsan16</a>&nbsp;</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=4&view=1">Forum PLUS</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Fria forum för seriösa diskussioner om allt möjligt.</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=16">Bank och Sparande</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247839">Sälja aktier</a> <a href="forum.php?thread_id=247839&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">565</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">18440</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 01:18</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=87044">hixaren</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=17">Bil / MC / Motorsport</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248311">Jag tål det inte</a> <a href="forum.php?thread_id=248311&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1510</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">26625</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 21:23</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=139360">Cowboy</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=94">Body modifications (piercing, tatuering m.m.)</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=235113">Tatuera &quot;UM&quot;?</a> <a href="forum.php?thread_id=235113&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1761</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">43606</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 14:10</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=157581">Panic</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=12">Datorspel och TV-spel</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=239385">Topp 3 spel!</a> <a href="forum.php?thread_id=239385&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">3083</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">77076</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:40</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=158232">Teal Crab</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=6">Datorer och IT</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248503">Msn och mp3 fungerar inkorrekt! Hjälp!</a> <a href="forum.php?thread_id=248503&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">7311</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">118024</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:02</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=157468">martin312</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=74">Djur och Husdjur</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248117">Vilka raser skulle ni vilja testa att korsa?</a> <a href="forum.php?thread_id=248117&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1340</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">52692</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:31</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=97621">Lanina</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=101">Drogdebatt</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=243431">Crystal-Meth</a> <a href="forum.php?thread_id=243431&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">446</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">22846</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:21</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=146603">Infraröd</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=81">Elektronikprylar och Telefoni</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247527">PS3 vs Blu-ray</a> <a href="forum.php?thread_id=247527&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1641</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">28464</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 00:25</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=133052">Fernan_king</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=71">Festivaler och Konserter</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248488">Hård Jävla Kärna III - World War [TMC]</a> <a href="forum.php?thread_id=248488&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1208</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">36881</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 08:30</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=70150">Gifted</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=11">Film, TV och Underhållning</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248316">favorit reklam?</a> <a href="forum.php?thread_id=248316&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">4518</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">120385</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:31</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=153750">JrL414_3</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=76">Graviditet, Föräldraskap och Adoption</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=236578">Unga mödrar....</a> <a href="forum.php?thread_id=236578&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1078</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">45362</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 10:27</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=156143">Hejjsan16</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=105">Historia</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=245448">Feodalism</a> <a href="forum.php?thread_id=245448&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">56</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1314</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: lör 10 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=115118">SilentScream</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=21">Hygien och Intimhygien</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248179">Hur ofta borstar du tänderna ?</a> <a href="forum.php?thread_id=248179&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1954</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">53798</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 14:15</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=160268">sweptaway</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=73">Konst och Grafik</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=222095">Ungdomars Fototråd!</a> <a href="forum.php?thread_id=222095&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">844</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">28630</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 09:03</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=147682">döög</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=66">Kortspel, Sällskapsspel och Lekar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248394">Hej :)</a> <a href="forum.php?thread_id=248394&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">223</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">5850</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 22:42</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=146274">ennie</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=25">Kroppen och Sjukdomar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247242">atopic Eksem</a> <a href="forum.php?thread_id=247242&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">8525</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">184452</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 13:54</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=159599">EVIL_GENIUS_IS_BACK</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=83">Litteratur</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=246587">Tips som verkar passa mig ?</a> <a href="forum.php?thread_id=246587&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">705</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">20575</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:37</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=96296">EmperorNero</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=33">Mat och Dryck</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=53687">vad har du ätit idag? (ej anorexi/bulimi)</a> <a href="forum.php?thread_id=53687&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">4837</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">185155</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:34</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=166158">Regnmoln</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=68">Missbruk och rehabilitering</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=245216">kompis</a> <a href="forum.php?thread_id=245216&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">2181</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">144241</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 12:51</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=166083">Glassbilen</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=77">Mobbning och Misshandel</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=246304">Sexuellt utnyttjad som barn?</a> <a href="forum.php?thread_id=246304&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">671</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">39680</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 01:33</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=105577">Jonnybravo91</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=3">Motgångar och Problem</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248496">Japan-fobi.</a> <a href="forum.php?thread_id=248496&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">4592</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">164793</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:42</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=134893">Chickfactor</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=5">Musik</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=1728">Vad lyssnar du på just nu tråden!</a> <a href="forum.php?thread_id=1728&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">9226</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">324876</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:33</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=153315">Noak_</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=9">Politik och Samhälle</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247928">Erfarenheter till er kommunister och andra som tycker om Kuba...</a> <a href="forum.php?thread_id=247928&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">4137</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">255757</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:30</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=79428">iddqd</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=29">Relationer, Samlevnad och Kompisar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248371">Tunga kändisar som ni känner?</a> <a href="forum.php?thread_id=248371&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">11524</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">318249</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:41</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=153750">JrL414_3</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=30">Religion och Etik</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=244916">Vad skulle få dig att tro på en skapare av universum?</a> <a href="forum.php?thread_id=244916&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1804</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">119512</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:31</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=147062">irenemaria</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=31">Resor och Upplevelser</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248183">Dags att boka årets semester...</a> <a href="forum.php?thread_id=248183&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1638</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">32026</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:35</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=162568">internet</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=84">Serietidningar och Manga</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=242442">Uppcon 09</a> <a href="forum.php?thread_id=242442&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">297</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">7213</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 13:29</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=160684">daisuki Duckieeee</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=7">Skola och Jobb</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248495">Vem är du i grupparbeten?</a> <a href="forum.php?thread_id=248495&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">6593</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">136838</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:16</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=158649">Jerkix</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=4">Skönhet, Utseende och Mode</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=236349">Långa tjejer är fula</a> <a href="forum.php?thread_id=236349&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">10933</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">346244</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:38</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=166158">Regnmoln</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=10">Sport och Fritid</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248463">Skatehall i Enköping?</a> <a href="forum.php?thread_id=248463&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1931</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">38991</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 23:47</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=165658">Jenja</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=92">Språk och Språkvetenskap</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=242132">ska mögel uttalas mögel eller möggel?</a> <a href="forum.php?thread_id=242132&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1053</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">37855</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:00</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=157468">martin312</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=34">Styrketräning och Frisksport</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248414">Träningsschema för gymmet, någon?</a> <a href="forum.php?thread_id=248414&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">3440</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">81577</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 14:05</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=121898">fraulinefrontline</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=82">Teater och Kultur</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=242910">grejen me teater</a> <a href="forum.php?thread_id=242910&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">156</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">3131</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 00:16</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=163338">OF 5</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=72">Vapen</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=212841">Vilken automatkarbin anser du vara bäst?</a> <a href="forum.php?thread_id=212841&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">272</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">14670</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 23:21</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=154845">typlsd</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=70">Vetenskap och Filosofi</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=246842">UFO-bilder <img src="/gfx/smilies/chocked.gif" alt="[chocked]" border=0 width=15 height=15>, äkta?</a> <a href="forum.php?thread_id=246842&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1303</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">54269</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 11:23</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=142876">SweetAlexa</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=85">Ätstörningar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=244951">hur reagerade era föreldrar?</a> <a href="forum.php?thread_id=244951&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">2675</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">117949</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:28</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=161338">mediakatt</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=39">Övriga diskussioner</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248339">Att hänga ut - Rätt eller fel?</a> <a href="forum.php?thread_id=248339&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">14015</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">450414</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:34</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=132899">kimberlyjoness</a>&nbsp;</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=8&view=1">Forum SEX</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Fria forum för diskussioner om sex, sexualitet och sexuella läggningar.</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=20">Homo- och Bisexualitet</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247772">Vad är din sexuella läggning?</a> <a href="forum.php?thread_id=247772&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1422</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">69004</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 14:44</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=149605">Grat</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=88">Könssjukdomar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248470">Vill inte gå till UM</a> <a href="forum.php?thread_id=248470&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">891</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">14330</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 00:56</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=88936">BLODÅDRA</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=87">Onani och Sexleksaker</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=240563">fingrar i rövhålet (killar)</a> <a href="forum.php?thread_id=240563&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1447</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">57047</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:37</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=96296">EmperorNero</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=75">Preventivmedel och Abort</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=227737">Funderar tamejfan på drastiska åtgärder...</a> <a href="forum.php?thread_id=227737&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1920</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">28155</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 12:48</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=166083">Glassbilen</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=8">Sex, Sexualitet och Sexuella fantasier</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248505">kiss fetish</a> <a href="forum.php?thread_id=248505&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">16023</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">526987</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:42</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=82838">cannabis</a>&nbsp;</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=3&view=1">Forum X</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Fria forum för mindre seriösa diskussioner...</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=91">Forumlekar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=114980">X lr X</a> <a href="forum.php?thread_id=114980&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1716</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">917227</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:42</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=96296">EmperorNero</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=24">Klotter</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248473">pearl jam-black</a> <a href="forum.php?thread_id=248473&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">36889</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1772766</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:42</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=89713">CUBIC_Cube</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=95">Länkar</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248489">Live-feed från Gaza - Bomber och Granater</a> <a href="forum.php?thread_id=248489&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1250</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">24706</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 07:30</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=128193">Mawns</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=67">Snusk</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247278">skulle mörknäs erkänna att han haft sex med dig?</a> <a href="forum.php?thread_id=247278&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">3044</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">243304</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 15:22</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=96296">EmperorNero</a>&nbsp;</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=6&view=1">Texter och berättelser</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Användares roliga historier, dikter, noveller etc.</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=65">Dikter</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248481">sexig vår</a> <a href="forum.php?thread_id=248481&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1939</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">22734</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 01:10</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=146274">ennie</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=90">Noveller och Berättelser</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=248484">min bästa vän lella</a> <a href="forum.php?thread_id=248484&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">451</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">6060</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I dag 01:36</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=112214">Lounge Act</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=63">Roliga historier</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=198043">Roliga historier utan poäng <img src="/gfx/smilies/tard.gif" alt="[tard]" border=0 width=15 height=15></a> <a href="forum.php?thread_id=198043&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">486</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">12975</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 21:57</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=165146">tigereyes</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=64">Sexnoveller</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247174">olle och ollonet</a> <a href="forum.php?thread_id=247174&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">534</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">11772</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: I går 20:22</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=166352">Pretty</a>&nbsp;</td></tr><tr><td class="forum_cat_sep" colspan=6><a class="forum_cat_cat" href="forum.php?category_id=9&view=1">Stängda forum</a><span class="forum_cat_cat">&nbsp;-&nbsp;</span><span class="forum_cat_desc">Stängda inaktuella forum.</span></td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=102">Fotbolls-EM 2008</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247799">tydgh</a> <a href="forum.php?thread_id=247799&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">31</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">1011</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: lör 10 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=115118">SilentScream</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=103">Hockey-VM 2008</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=242098">Tankar inför VM</a> <a href="forum.php?thread_id=242098&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">17</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">408</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: fre 26 dec 2008</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=115118">SilentScream</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=89">Fotbolls-VM 2006</a><br>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">141</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">5003</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: tor 13 jul 2006</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=56908">met0xy</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=104">Sommar-OS i Beijing 2008</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247888">PIZZA <img src="/gfx/smilies/cry.gif" alt="[cry]" border=0 width=15 height=15></a> <a href="forum.php?thread_id=247888&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">20</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">373</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: tor  8 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_on" href="user_info.php?user_id=144581">Link</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_unread.gif" title="Detta forum innehåller olästa trådar" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=98">Idol 2007</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=247388"><img src="/gfx/smilies/mad.gif" alt="[mad]" border=0 width=15 height=15></a> <a href="forum.php?thread_id=247388&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">88</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">2203</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: lör 10 jan 2009</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=115118">SilentScream</a>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=97">Ungdomar TV</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=187411">Ungdomar.se på Facebook</a> <a href="forum.php?thread_id=187411&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">8</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">967</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: fre 26 dec 2008</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=115118">SilentScream</a>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=93">Idol 2006</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=129307">[Markus (hjärta) Felicia?]</a> <a href="forum.php?thread_id=129307&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">137</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">5606</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: ons 13 dec 2006</span><br>&nbsp;</td></tr><tr class="forum_cat_tbr2"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=78">OS i Turin 2006</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=73169">[Vi kan bli av med OS-Guldet]</a> <a href="forum.php?thread_id=73169&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">38</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr2_td_dark" align="center">1247</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: mån  6 mar 2006</span><br>&nbsp;</td></tr><tr class="forum_cat_tbr1"><td class="forum_cat_tbr_td" align="center"><img src="/gfx/forum_allread.gif" title="Inga nya inlägg" width=13 height=13></td><td class="forum_cat_tbr_td"><a class="forum_cat_forum" href="forum.php?forum_id=79">Val 2006</a><br><span class="forum_info1">Senaste: </span><a class="forum_info2" href="forum.php?thread_id=89587">[Vänsterpartister snattar mest!]</a> <a href="forum.php?thread_id=89587&page=-1#bottom"><img title="Till sista inlägget" src="/gfx/forum_jump.gif" width=9 height=7 border=0></a>&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">234</td><td class="forum_cat_tbr_td" align="center">&nbsp;</td><td class="forum_cat_tbr1_td_dark" align="center">14753</td><td class="forum_cat_tbr_td" style="padding-left:15px;" width="180"><span class="forum_info2">Ändrad: mån 25 sep 2006</span><br><span class="forum_info2">av </span><a class="forum_user_off" href="user_info.php?user_id=59264">passaro</a>&nbsp;</td></tr></table>      </td></tr>

      <tr><td align="center" class="page_frame_color">
        <table width=600 border=0 cellpadding=0 cellspacing=0><tr>
        <td class="page_footer"><a name="bottom"></a>Copyright © 2000-2007, <a href="http://umit.se" target="_blank">UMIT AB</a>, Alla rättigheter reserverade - <a href="about_cookies.php">Om cookies</a> - <a href="rulez.php">Ungdomar.se's regler</a></td>
        <td valign="middle" align="right"><a href="/about_rss.php"><img src="/gfx/rss.gif" alt="RSS" width=34 height=13 border=0></a></td>
        </tr></table>

      </td></tr>
    </table>
  </td>
  
  <td width="260" valign="top">
    <!-- Ad pane -->
    <table width="260" border=0 cellspacing=0 cellpadding=0 class="page_frame_color">
      <tr><td align="center"><img src="/gfx/1/right_list_top.gif" width=250 height=30><br/><div style="margin-bottom:5px;"><SCRIPT type="text/javascript">
  <!--
  OAS_AD('Right1');
  //-->
  </SCRIPT></div><div style="margin-bottom:5px;"><SCRIPT type="text/javascript">
  <!--
  OAS_AD('Right2');
  //-->
  </SCRIPT></div><div style="margin-bottom:5px;"><SCRIPT type="text/javascript">
  <!--
  OAS_AD('Right3');
  //-->
  </SCRIPT></div><div style="margin-bottom:5px;"><SCRIPT type="text/javascript">
  <!--
  OAS_AD('Right4');
  //-->
  </SCRIPT></div><div style="margin-bottom:5px;"><SCRIPT type="text/javascript">
  <!--
  OAS_AD('Right5');
  //-->
  </SCRIPT></div><div style="padding:15px;"><div style="text-align:center;"><img src="gfx/spotlight.gif" alt="" /></div><br /><table style="margin-bottom:10px;" width="230" cellspacing="0" cellpadding="0"><tr><td valign="top">

    <table border="0" cellpadding="0" cellspacing="0" style=""><tr><td class="image_border"><a href="user_images.php?user_id=161227&folder_id=9272"><img src="thumbs/82/39/ui_081c50fc7a28d76735ec5cd97c5f44b7.jpg" alt="" /></a></td></tr></table></td>
    <td valign="top" style="color:#979797;font-size:9px;">
    <b><a href="user_images.php?user_id=161227&folder_id=9272">Game over.</a></b><br /><br />
    <b>Av:</b> <b><a href="user_info.php?user_id=161227">Lovelips</a></b><br/>
    <b>Visningar:</b> 496</td></tr></table><div style="background-image:url(/gfx/pane_separator_small.gif);"><img src="/gfx/1x1.gif" width="1" height="7"></div><div style="color:#979797;text-align:left;margin-top:10px;margin-bottom:10px;font-size:9px;"><table border="0" cellpadding="0" cellspacing="0" style=""><tr><td class="image_border"><a href="blogg.php?user_id=86776"><img src="/images/75/32/blogg_86776.jpg" width="210" height="65" border="0" alt=""></a></td></tr></table><div style="margin-top:4px;margin-bottom:4px;"><b><a href="blogg.php?user_id=86776&blogg_id=48974">Suck</a></b></div>

          <b><a href="user_info.php?user_id=86776">bimbo15</a></b> | fre  6 apr 2007 23:48</div><div style="background-image:url(/gfx/pane_separator_small.gif);"><img src="/gfx/1x1.gif" width="1" height="7"></div><table style="margin-top:10px;" width="230" cellspacing="0" cellpadding="0"><tr><td valign="top">
          <table border="0" cellpadding="0" cellspacing="0" style=""><tr><td class="image_border"><a href="user_info.php?user_id=81374"><img src="images/62/41/ava_81374.jpg" width="82" height="82" alt="" /></a></td></tr></table>
          </td><td valign="top" style="color:#979797;font-size:9px;">
          <b><a style="font-size:11px;" href="user_info.php?user_id=81374">SebastianE</a></b><br /><br />
          <b>Inloggningar</b> 2755<br />

          <b>Skapade trådar</b> <a href="forum_user.php?user_id=81374&type=1">208</a><br />
          <b>Postade inlägg</b> <a href="forum_user.php?user_id=81374&type=2">7426</a><br />
          <b>Skickade PM</b> 494<br />
          <b>Besök på Min sida</b> 3687
          </td></tr></table>      </td></tr>

            <tr><td align="center" style="padding-top:5px;"><img src="/gfx/1/right_list_bottom.gif" width=250 height=9><br/></td></tr>
      <tr><td align="center" class="page_footer">Vill du annonsera på Ungdomar.se? <a href="about_us.php">Klicka här!</a></td></tr>
    </table>
  </td>
</tr>
</table>
</div>
<br>
<div name="tipDiv" id="tipDiv" style="position:absolute;z-index:100;top:200px;left:50%;width:388px;margin-left:-198px;filter:alpha(opacity=90);-moz-opacity:.90;opacity:.90;background-color:#2B2A29;padding:16px;display:none;">
  <div style="font-size:12px;font-weight:bold;color:#ffffff;padding-bottom:6px;">Tipsa en vän</div>

  <form name="tipForm" id="tipForm" method="post" action="tip.php">
  <div style="color:#ffffff;font-size:11px;line-height:16px;">
  Du vill tipsa en vän om sidan: <a href="http://ungdomar.se/forum.php">http://ungdomar.se/forum.php</a><br /><br />
  Fyll i din väns e-postadress, ett meddelande och klicka på tipsa. För att tipsa flera vänner på samma gång skriver du in fler e-postadresser separerat med ett komma. Ex. [EMAIL="abc123@ungdomar.se"]abc123@ungdomar.se[/EMAIL], [EMAIL="abc456@ungdomar.se"]abc456@ungdomar.se[/EMAIL].<br /><br /> Du kan även ange ett namn för mailadressen du anger, detta gör du genom att separera mailadressen och namnet med ett mellanslag. Ex.  [EMAIL="abc123@ungdomar.se"]abc123@ungdomar.se[/EMAIL] John Doe, [EMAIL="abc456@ungdomar.se"]abc456@ungdomar.se[/EMAIL], [EMAIL="abc789@ungdomar.se"]abc789@ungdomar.se[/EMAIL] polarn. <br />Här får första mailadressen namnet John Doe andra får inget namn och tredje får namnet polarn.
  </div>
  <div style="font-weight:bold;color:#9B9B9B;font-size:11px;"><br />
    E-postadress(er):<br />

    <input type="text" name="tipEmails" id="tipEmails" style="width:270px;" /><br />
    <br />
    Meddelande:<br />
    <textarea name="tipMessage" id="tipMessage" style="width:350px;height:150px;"></textarea><br /><br /><br />
    <div style="text-align:right;">
      <button type="button" class="button_gray" onclick="javascript:vh('tipDiv');">Ångra</button>&nbsp;<button type="submit" class="button_active">Tipsa</button>
    </div>

  </div>
  <input type="hidden" name="tipAddress" id="tipAddress" value="http://ungdomar.se/forum.php" />
  <input type="hidden" name="tipUser" id="tipUser" value="162005" />
  </form>
</div>

<!-- GOOGLE ANALYTICS -->
<script src="http://umit.se/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-4206765-2";
urchinTracker();
</script>

</body>

</html>
<script type="text/javascript" language="JavaScript" src="/js/wz_tooltip.js"></script>
```

EDIT: Oh! I see it now. It must have missed the span class-part. Sorry about that.

---

### Post by guilherme08 on 2009-01-12
So that's why the regexp seemed to be completely wrong. Okay then, I'm glad it all works, good luck with your script!

---

### Post by Nevon on 2009-01-12
> **guilherme08 said:**
> So that's why the regexp seemed to be completely wrong. Okay then, I'm glad it all works, good luck with your script!

Thank you very much for your help. There are still some modifications do to, but except for the urlencode part, I think I can handle most of it myself.

---

