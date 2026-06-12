---
title: "wget local offline links not working...?"
date: 2007-08-30
forum: Programming Talk
---

### Post by Hopeless on 2007-08-30
Hi Ya,

wget is great im not!?

problem:

Firefox can't find the file at /home/shane/www.web.com/forum/topic.asp?TOPIC_ID=2042.

load file and is:
file:///home/shane/www.web.com/forum/topic.asp%3FTOPIC_ID%3D2042

the ? has changed to a %3 i tried in .wgetrc:
restrict-file-names=nocontrol

no luck...

what can i do????

thanks...

---

### Post by bashologist on 2007-08-30
I might not understand your problem but I think the question mark turns into the "%3F", and the equals sign turn into "%3D", which as far as I know shouldn't cause problems with anything. 

Could the space in between the "T" and the "O" be causing the problem? Try to copy and paste the address again in your browser? Is there anything strange about the file path like is it a symbolic link?

---

### Post by Hopeless on 2007-08-31
Sorry must have been my typing error...[[COLOR="Red"]no it not its this forum, there is no spaces in gedit or visually, when i edit my post there is no space[/COLOR]]

Firefox:
/home/shane/www.website.com/forum/topic.asp?TOPIC_ID=2042

address bar in firefox...
/home/shane/www.website.com/forum/topic.asp?TOPIC_ID=2042

manually load file...in addressbar is...
/home/shane/www.website.com/forum/topic.asp%3FTOPIC_ID%3D2042

the file in the folder is named:
topic.asp?TOPIC_ID=2042[/QUOTE]

firefox complains it's not there?

attached tester2.jpg which is just after i click the link, tester1.jpg is the manually loaded file...HTH

what did i do wrong? stumped me..

---

### Post by Hopeless on 2007-09-02
Please help still not working.... [COLOR="Red"]is it a firefox problem or wgets? or mine[/COLOR] ;)

me thinks [COLOR="Red"]--restrict-file-names=mode[/COLOR] section is the answer....but don't know what ?

tried :
--restrict-file-names=windows
--restrict-file-names=unix
--restrict-file-names=unix,nocontrol
--restrict-file-names=nocontrol
no luck soooo far...

i think the link in the downloaded page is refering to the '?' and the '=' and the page is '%3F' and '%3D' is the downloaded links converted??? i use convert-links = on 
can't move on.. :( :(

Many thanks for this...

---

### Post by cwaldbieser on 2007-09-02
> **Hopeless said:**
> Please help still not working.... [COLOR="Red"]is it a firefox problem or wgets? or mine[/COLOR] ;)

me thinks [COLOR="Red"]--restrict-file-names=mode[/COLOR] section is the answer....but don't know what ?

tried :
--restrict-file-names=windows
--restrict-file-names=unix
--restrict-file-names=unix,nocontrol
--restrict-file-names=nocontrol
no luck soooo far...

i think the link in the downloaded page is refering to the '?' and the '=' and the page is '%3F' and '%3D' is the downloaded links converted??? i use convert-links = on 
can't move on.. :( :(

Many thanks for this...

Could you maybe give us the original wget command you used to download the pages so we can also download them and experiment?

---

### Post by Hopeless on 2007-09-03
sure here goes:

wget -rl1 -U Mozilla 'www.somewebsite.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1'

.wgetrc:
robots = off
randomwait = on
reject = topic.asp?whichpage*,*FORUM_ID=11,*FORUM_ID=34,*FORUM_ID=44,*FORUM_ID=51,*FORUM_ID=53,*FORUM_ID=5,*FORUM_ID=57,*FORUM_ID=6,*FORUM_ID=7, button_logout.gif,catbg.gif,fishtank.swf,footerback.gif,headbg.gif,headerback.gif,icon_bar.gif,icon_blank.gif,icon_folder_closed_topic.gif,icon_folder.gif,icon_folder_hot.gif,icon_folder_locked2.gif,icon_folder_locked_f.gif,icon_folder_new.gif,icon_folder_new_topic2.gif,icon_folder_new_topic.gif,icon_folder_open.gif,icon_folder_open_topic.gif,icon_folder_sticky.gif,icon_folder_sticky_locked.gif,icon_go_up.gif,icon_group.gif,icon_lastpost.gif,icon_mi_10.gif,icon_mi_11.gif,icon_mi_13.gif,icon_mi_14.gif,icon_mi_1.gif,icon_mi_2.gif,icon_mi_4.gif,icon_mi_6.gif,icon_mi_7.gif,icon_mi_8.gif,icon_mi_9.gif,icon_minus.gif,icon_navmenu_guestbook.gif,icon_navmenu_help.gif,icon_navmenu_home.gif,icon_navmenu_member.gif,icon_navmenu_news.gif,icon_navmenu_search.gif,icon_navmenu_url.gif,icon_pencil.gif
accept = topic.asp*,forum.asp*,*FORUM_ID=35* -A gif,jpg,pdf,zip,rar,tif
load_cookies = ~/.mozilla/firefox/xjg5nmlx.default/cookies.txt
limit-rate = 20K 
no_parent = on

i even cut n pasted the name firefox wanted from the file not found to the name of the file and it still can't find it??? weird !!

hey do me a favor create a file with a link to any file named 
topic.asp?TOPIC_ID=2042
see if you can load it?

really need help on this and appreciate you effort helping me
:)

---

### Post by Hopeless on 2007-09-03
Is it Ubuntu?

I just made a html with a link 
topic.asp?TOPIC_ID=2042
and it wont load!?

how can i be fixin this ya'll?

Taa..

---

### Post by cwaldbieser on 2007-09-03
> **Hopeless said:**
> Is it Ubuntu?

I just made a html with a link 
topic.asp?TOPIC_ID=2042
and it wont load!?

how can i be fixin this ya'll?

Taa..
OK, I think I figured out what you are experiencing.  Your browser probably does not know how to display a local file with extension ".asp".  When you are surfing online, a web server processes the ASP page you request and servers your browser HTML content.  Your browser likely does not know that the pages you have are HTML.  The easiest way to fix this is to use the -E option from the wget man pages:
> 
       -E
       --html-extension
           If a file of type application/xhtml+xml or text/html is downloaded
           and the URL does not end with the regexp \.[Hh][Tt][Mm][Ll]?, this
           option will cause the suffix .html to be appended to the local
           filename.  This is useful, for instance, when you're mirroring a
           remote site that uses .asp pages, but you want the mirrored pages
           to be viewable on your stock Apache server.  Another good use for
           this is when you're downloading CGI-generated materials.  A URL
           like [http://site.com/article.cgi?25](http://site.com/article.cgi?25) will be saved as arti-
           cle.cgi?25.html.

           Note that filenames changed in this way will be re-downloaded every
           time you re-mirror a site, because Wget can't tell that the local
           X.html file corresponds to remote URL X (since it doesn't yet know
           that the URL produces output of type text/html or applica-
           tion/xhtml+xml.  To prevent this re-downloading, you must use -k
           and -K so that the original version of the file will be saved as
           X.orig.


---

### Post by Hopeless on 2007-09-04
Hi,

will the links change also to point to the .html extention?

thanks..

---

### Post by cwaldbieser on 2007-09-04
> **Hopeless said:**
> Hi,

will the links change also to point to the .html extention?

thanks..

I believe so.  Why not try it with a few pages and see?

---

### Post by Hopeless on 2007-09-05
tried but no luck wget is not converting the links to point to the new .html file eg.
file is forum.asp?FORUM_ID=36.html
link is forum.asp?FORUM_ID=36

hate to say this but firefox loaded the pages in windowz i think its a operating system instead of wget....what do you think?

regards..

---

### Post by cwaldbieser on 2007-09-05
> **Hopeless said:**
> tried but no luck wget is not converting the links to point to the new .html file eg.
file is forum.asp?FORUM_ID=36.html
link is forum.asp?FORUM_ID=36

hate to say this but firefox loaded the pages in windowz i think its a operating system instead of wget....what do you think?

regards..

Did you use the -k option?  What is the exact command line you are using?

---

### Post by Hopeless on 2007-09-05
doh!

no i used:
html-extension = on
in my .wgetrc file...

is it the same...??

thanks..

---

### Post by cwaldbieser on 2007-09-06
Try this:
```

$ wget -E -k -r 'http://url/to/website'

```
Replace the URL between the single quotes.
The -E flag changes the pages to have .html extensions.
The -k flag converts the links.
The -r flag recursively follows links.

Try "man wget" for a ton of more options,

---

### Post by Hopeless on 2007-09-06
cwaldbieser - thanks works ok.. loads first without the .html then loads the .html file...have to press the back button twice...

but hey i really don't want the .html extension...

i noticed when i used the -k by itself does nothing... but with the -E the '?' changes to a '%3F' so i took off the .html file since i have the same file without the .html and pluged it into the nav bar in firefox and it loaded !!! GREAT i thought...

how can i just convert the '?' in each link to "%3F"?

i tried already
--restrict-file-names=windows
--restrict-file-names=unix
--restrict-file-names=unix,nocontrol
--restrict-file-names=nocontrol

do you think combo with the -k would work??

thanks

---

### Post by Hopeless on 2007-09-06
i think i found the prob highlighted in red

td width="50%" style="cursor: hand" onClick=[COLOR="Red"]"window.location.href='topic.asp?TOPIC_ID=23'" [/COLOR]class="button" valign="middle" align="left">                <font face="Verdana, Arial, Helvetica" size="2" color="#000000">Sticky:  <span class="spnMessageText">[COLOR="Red"]<a href="topic.asp%3FTOPIC_ID=23.html">click here</a>[/COLOR]</span>&nbsp;</font>

how can i change the window.location.href?

or convert the ? to a %3F ???

---

### Post by cwaldbieser on 2007-09-07
> **Hopeless said:**
> i think i found the prob highlighted in red

td width="50%" style="cursor: hand" onClick=[COLOR="Red"]"window.location.href='topic.asp?TOPIC_ID=23'" [/COLOR]class="button" valign="middle" align="left">                <font face="Verdana, Arial, Helvetica" size="2" color="#000000">Sticky:  <span class="spnMessageText">[COLOR="Red"]<a href="topic.asp%3FTOPIC_ID=23.html">click here</a>[/COLOR]</span>&nbsp;</font>

how can i change the window.location.href?

or convert the ? to a %3F ???

I am not sure that wget can help you rewrite the HTML/javascript.  If you know some scripting, you could probably use an HTML parser to look for onclick attributes containing URLs and tweak them.

---

### Post by KungFuGeek on 2008-06-05
I know its a year later, but as I ran into the same problem i figure others might as well.

I had URLs being called in javascript that were something like this

```
 onclick=\"location.href=\'index.asp?page=webpage&webpagekey=22\';\"
```



What i did is run

```
perl -pi -e 's/index.asp\?/index.asp%3f/g' *.html
```

in the directory after i used

```
wget -E -k -p -nH -r www.example.com
```

I also had to add .html to all the links in the javascript so i used this to do that

```
perl -pi -e 's/(webpagekey=[0123456789]{1,})\\/$1\.html\\/g' *.html
```

now im sure if a perl or regex guru sees this they may have better ways of doing it, but it worked for me.

---

