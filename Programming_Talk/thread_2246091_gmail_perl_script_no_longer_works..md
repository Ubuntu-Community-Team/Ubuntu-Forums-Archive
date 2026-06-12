---
title: "gmail perl script no longer works."
date: 2014-09-28
forum: Programming Talk
---

### Post by CantankRus on 2014-09-28
I have used this perl script for gmail with conky for a number of years but recently
it always returns [COLOR="#FF0000"]0[/COLOR] emails when **there is** unread emails.
_gmail.pl_
```
#!/usr/bin/perl

## Origin of script## http://ubuntuforums.org/showthread.php?t=680265

#########################################################
##### WARNING: Change name and password if posting!! ####
#########################################################

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="username"; #username for gmail account
$pass="password"; #password for gmail account
$file="/tmp/gmail.html"; #temporary file to store gmail

#wrap format for subject
$Text::Wrap::columns=50; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

#limit the number of emails to be displayed
$emails=4; #if -1 display all emails

&passwd; #give password the proper url character encoding

switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		if ($new>0){
			my $size=@from;
			if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "\nSender: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote."\n";
				print wrap($initial_tab, $subsequent_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			$size=@from;
			if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	} 	
	case "e" { #print number of new emails, $from, and $subj
		&gmail;
		if($new==0){print "You have no new emails.\n";}
		else{
			print "You have $new new email(s).\n";
			my $size=@from;
			if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "From: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote;
				print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			$size=@from;
			if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	}
	else {
		print "Usage Error: gmail.pl <option>\n";
		print "\tn displays number of new emails\n";
		print "\ts displays from line and subject line for each new email.\n";
		print "\te displays the number of new emails and from line plus \n";
		print "\t\tsubject line for each new email.\n";
	} #didn't give proper option
}

sub gmail{
	if(!(-e $file)){ #create file if it does not exists
		`touch $file`;
	} 

	#get new emails
	`wget -O - https://$user:$pass\@mail.google.com/mail/feed/atom --no-check-certificate> $file`;

	open(IN, $file); #open $file

	my $i=0; #initialize count
	$new=0; #initialize new emails to 0

	my $flag=0;

	while(<IN>){ #cycle through $file
		if(/<entry>/){$flag=1;}
		elsif(/<fullcount>(\d+)<\/fullcount>/){$new=$1;} #grab number of new emails
		elsif($flag==1){ 
			if(/<title>.+<\/title>/){push(@subj, &msg);} #grab new email titles
			elsif(/<name>(.+)<\/name>/){push(@from, $1); $flag=0;} #grab new email from lines
		}
	}

	close(IN); #close $file
}

sub passwd{ #change to url escape codes in password
	#URL ESCAPE CODES
	$_=$pass;
	s/\%/\%25/g;
	s/\#/\%23/g;
	s/\$/\%24/g;
	s/\&/\%26/g;
	s/\//\%2F/g;
	s/\:/\%3A/g;
	s/\;/\%3B/g;
	s/\</\%3C/g;
	s/\=/\%3D/g;
	s/\>/\%3E/g;
	s/\?/\%3F/g;
	s/\@/\%40/g;
	s/\[/\%5B/g;
	s/\\/\%5C/g;
	s/\]/\%5D/g;
	s/\^/\%5E/g;
	s/\`/\%60/g;
	s/\{/\%7B/g;
	s/\|/\%7C/g;
	s/\}/\%7D/g;
	s/\~/\%7E/g;
	$pass=$_;
}

sub msg{
	#THE HTML CODED CHARACTER SET [ISO-8859-1]
	chomp; s/<title>(.+)<\/title>/$1/; #get just the subject
	#now replace any special characters
	s/\&\#33\;/!/g;        #Exclamation mark
	s/\&\#34\;/"/g; s/\&quot\;/"/g;      #Quotation mark
	s/\&\#35\;/#/g;        #Number sign
	s/\&\#36\;/\$/g;        #Dollar sign
	s/\&\#37\;/%/g;        #Percent sign
	s/\&\#38\;/&/g; s/\&amp\;/&/g;        #Ampersand
	s/\&\#39\;/'/g;        #Apostrophe
	s/\&\#40\;/(/g;        #Left parenthesis
	s/\&\#41\;/)/g;        #Right parenthesis
	s/\&\#42\;/*/g;        #Asterisk
	s/\&\#43\;/+/g;        #Plus sign
	s/\&\#44\;/,/g;        #Comma
	s/\&\#45\;/-/g;        #Hyphen
	s/\&\#46\;/./g;        #Period (fullstop)
	s/\&\#47\;/\//g;        #Solidus (slash)
	s/\&\#58\;/:/g;        #Colon
	s/\&\#59\;/\;/g;        #Semi-colon
	s/\&\#60\;/</g; s/\&lt\;/</g;        #Less than
	s/\&\#61\;/=/g;        #Equals sign
	s/\&\#62\;/>/g; s/\&gt\;/>/g;        #Greater than
	s/\&\#63\;/\?/g;        #Question mark
	s/\&\#64\;/\@/g;        #Commercial at
	s/\&\#91\;/\[/g;        #Left square bracket
	s/\&\#92\;/\\/g;        #Reverse solidus (backslash)
	s/\&\#93\;/\]/g;        #Right square bracket
	s/\&\#94\;/\^/g;        #Caret
	s/\&\#95\;/_/g;        #Horizontal bar (underscore)
	s/\&\#96\;/\`/g;        #Acute accent
	s/\&\#123\;/\{/g;        #Left curly brace
	s/\&\#124\;/|/g;        #Vertical bar
	s/\&\#125\;/\}/g;        #Right curly brace
	s/\&\#126\;/~/g;        #Tilde
	s/\&\#161\;/¡/g;        #Inverted exclamation
	s/\&\#162\;/¢/g;        #Cent sign
	s/\&\#163\;/£/g;        #Pound sterling
	s/\&\#164\;/¤/g;        #General currency sign
	s/\&\#165\;/¥/g;        #Yen sign
	s/\&\#166\;/¦/g;        #Broken vertical bar
	s/\&\#167\;/§/g;        #Section sign
	s/\&\#168\;/¨/g;        #Umlaut (dieresis)
	s/\&\#169\;/©/g; s/\&copy\;/©/g;        #Copyright
	s/\&\#170\;/ª/g;        #Feminine ordinal
	s/\&\#171\;/«/g;        #Left angle quote, guillemotleft
	s/\&\#172\;/¬/g;        #Not sign
	s/\&\#174\;/®/g;        #Registered trademark
	s/\&\#175\;/¯/g;        #Macron accent
	s/\&\#176\;/°/g;        #Degree sign
	s/\&\#177\;/±/g;        #Plus or minus
	s/\&\#178\;/²/g;        #Superscript two
	s/\&\#179\;/³/g;        #Superscript three
	s/\&\#180\;/´/g;        #Acute accent
	s/\&\#181\;/µ/g;        #Micro sign
	s/\&\#182\;/¶/g;        #Paragraph sign
	s/\&\#183\;/·/g;        #Middle dot
	s/\&\#184\;/¸/g;        #Cedilla
	s/\&\#185\;/¹/g;        #Superscript one
	s/\&\#186\;/º/g;        #Masculine ordinal
	s/\&\#187\;/»/g;        #Right angle quote, guillemotright
	s/\&\#188\;/¼/g; s/\&frac14\;/¼/g;       # Fraction one-fourth
	s/\&\#189\;/½/g; s/\&frac12\;/½/g;       # Fraction one-half
	s/\&\#190\;/¾/g; s/\&frac34\;/¾/g;       # Fraction three-fourths
	s/\&\#191\;/¿/g;        #Inverted question mark
	s/\&\#192\;/À/g;        #Capital A, grave accent
	s/\&\#193\;/Á/g;        #Capital A, acute accent
	s/\&\#194\;/Â/g;        #Capital A, circumflex accent
	s/\&\#195\;/Ã/g;        #Capital A, tilde
	s/\&\#196\;/Ä/g;        #Capital A, dieresis or umlaut mark
	s/\&\#197\;/Å/g;        #Capital A, ring
	s/\&\#198\;/Æ/g;        #Capital AE dipthong (ligature)
	s/\&\#199\;/Ç/g;        #Capital C, cedilla
	s/\&\#200\;/È/g;        #Capital E, grave accent
	s/\&\#201\;/É/g;        #Capital E, acute accent
	s/\&\#202\;/Ê/g;        #Capital E, circumflex accent
	s/\&\#203\;/Ë/g;        #Capital E, dieresis or umlaut mark
	s/\&\#204\;/Ì/g;        #Capital I, grave accent
	s/\&\#205\;/Í/g;        #Capital I, acute accent
	s/\&\#206\;/Î/g;        #Capital I, circumflex accent
	s/\&\#207\;/Ï/g;        #Capital I, dieresis or umlaut mark   
	s/\&\#208\;/Ð/g;        #Capital Eth, Icelandic
	s/\&\#209\;/Ñ/g;        #Capital N, tilde
	s/\&\#210\;/Ò/g;        #Capital O, grave accent
	s/\&\#211\;/Ó/g;        #Capital O, acute accent
	s/\&\#212\;/Ô/g;        #Capital O, circumflex accent
	s/\&\#213\;/Õ/g;        #Capital O, tilde
	s/\&\#214\;/Ö/g;        #Capital O, dieresis or umlaut mark
	s/\&\#215\;/×/g;        #Multiply sign
	s/\&\#216\;/Ø/g;        #Capital O, slash
	s/\&\#217\;/Ù/g;        #Capital U, grave accent
	s/\&\#218\;/Ú/g;        #Capital U, acute accent
	s/\&\#219\;/Û/g;        #Capital U, circumflex accent
	s/\&\#220\;/Ü/g;        #Capital U, dieresis or umlaut mark
	s/\&\#221\;/Ý/g;        #Capital Y, acute accent
	s/\&\#222\;/Þ/g;        #Capital THORN, Icelandic
	s/\&\#223\;/ß/g;        #Small sharp s, German (sz ligature)
	s/\&\#224\;/à/g;        #Small a, grave accent
	s/\&\#225\;/á/g;        #Small a, acute accent
	s/\&\#226\;/â/g;        #Small a, circumflex accent
	s/\&\#227\;/ã/g;        #Small a, tilde
	s/\&\#228\;/ä/g;        #Small a, dieresis or umlaut mark
	s/\&\#229\;/å/g;        #Small a, ring
	s/\&\#230\;/æ/g;        #Small ae dipthong (ligature)
	s/\&\#231\;/ç/g;        #Small c, cedilla
	s/\&\#232\;/è/g;        #Small e, grave accent
	s/\&\#233\;/é/g;        #Small e, acute accent
	s/\&\#234\;/ê/g;        #Small e, circumflex accent
	s/\&\#235\;/ë/g;        #Small e, dieresis or umlaut mark
	s/\&\#236\;/ì/g;        #Small i, grave accent
	s/\&\#237\;/í/g;        #Small i, acute accent
	s/\&\#238\;/î/g;        #Small i, circumflex accent
	s/\&\#239\;/ï/g;        #Small i, dieresis or umlaut mark
	s/\&\#240\;/ð/g;        #Small eth, Icelandic
	s/\&\#241\;/ñ/g;        #Small n, tilde
	s/\&\#242\;/ò/g;        #Small o, grave accent
	s/\&\#243\;/ó/g;        #Small o, acute accent
	s/\&\#244\;/ô/g;        #Small o, circumflex accent
	s/\&\#245\;/õ/g;        #Small o, tilde
	s/\&\#246\;/ö/g;        #Small o, dieresis or umlaut mark
	s/\&\#247\;/÷/g;        #Division sign
	s/\&\#248\;/ø/g;        #Small o, slash
	s/\&\#249\;/ù/g;        #Small u, grave accent
	s/\&\#250\;/ú/g;        #Small u, acute accent
	s/\&\#251\;/û/g;        #Small u, circumflex accent
	s/\&\#252\;/ü/g;        #Small u, dieresis or umlaut mark
	s/\&\#253\;/ý/g;        #Small y, acute accent
	s/\&\#254\;/þ/g;        #Small thorn, Icelandic
	s/\&\#255\;/ÿ/g;        #Small y, dieresis or umlaut mark
	s/^\s+//;
	return $_;
}
```

```
@Trusty:~$ **perl ~/scripts/gmail.pl n**
--2014-09-28 22:19:41--  https://[COLOR="#808080"]xxxxxx[/COLOR]:*password*@mail.google.com/mail/feed/atom
Resolving mail.google.com (mail.google.com)... 74.125.237.150, 2404:6800:4006:805::1015
Connecting to mail.google.com (mail.google.com)|74.125.237.150|:443... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to mail.google.com:443.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: 'STDOUT’

    [ <=>                                                                    ] 1,465       --.-K/s   in 0.001s  

2014-09-28 22:19:43 (2.09 MB/s) - written to stdout [1465]

[COLOR="#FF0000"]0[/COLOR]

```

I can access gmail ok with the following python script which can be run with 
```
python /path/to/check-gmail.py [COLOR="#808080"]<username> <password>[/COLOR] 3
```
_check-gmail.py_
```
# check-gmail.py -- A command line util to check GMail -*- Python -*-
## modified to display mailbox summary for conky

# ======================================================================
# Copyright (C) 2006 Baishampayan Ghose <b.ghose@ubuntu.com>
# Modified 2008 Hunter Loftis <hbloftis@uncc.edu>
# Time-stamp: Mon Jul 31, 2006 20:45+0530
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================

import sys
import urllib             # For BasicHTTPAuthentication
import feedparser         # For parsing the feed
from textwrap import wrap

_URL = "https://mail.google.com/gmail/feed/atom"

name = sys.argv[1]
pword = sys.argv[2]
maxlen = sys.argv[3]

urllib.FancyURLopener.prompt_user_passwd = lambda self, host, realm: (name, pword)
	
def auth():
    '''The method to do HTTPBasicAuthentication'''
    opener = urllib.FancyURLopener()
    f = opener.open(_URL)
    feed = f.read()
    return feed

def readmail(feed, maxlen):
	'''Parse the Atom feed and print a summary'''
	atom = feedparser.parse(feed)
	print '${font GE Inspira:bold:size=16}${color  lightgrey}%s@gmail.com ${color orange}(%s Unread)${font}\n' % (name, len(atom.entries))
	for i in range(min(len(atom.entries), maxlen)):
		print '${color  lightgrey}From: ${color}%s' % atom.entries[i].author
		print '				${color  lightgrey}Title: ${color}"%s"' % atom.entries[i].title
	if len(atom.entries) > maxlen:
		print ' ${color}more...'

if __name__ == "__main__":
    f = auth()  # Do auth and then get the feed
    readmail(f, int(maxlen)) # Let the feed be chewed by feedparser
```

Anyone know why the perl script no longer works?

---

### Post by tgalati4 on 2014-09-28
To improve security, perhaps gmail is enforcing certificates?

Your perl script:

> 	`wget -O - https://$user:$pass\@mail.google.com/mail/feed/atom** --no-check-certificate**> $file`;

One test you could try:

Log into gmail in a browser and leave it open.  Then try your perl script.  If your session is open and authenticated, then it might work.  If you close your session, you lose authentication and the perl script fails.  I don't know of a work-around.

---

### Post by vasa1 on 2014-09-28
```
curl -u username:password --silent "https://mail.google.com/mail/feed/atom" | perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'
```works for me with my browser closed. I have another thread here on curl/perl/gmail here: [http://ubuntuforums.org/showthread.php?t=2246083](http://ubuntuforums.org/showthread.php?t=2246083) :)

---

### Post by CantankRus on 2014-09-28
**@tgalati4**
Still returns 0 when I know there are 2 unread emails...thanks.


**@vasa1**
The curl code works...
```
@Trusty:~$ curl -u [COLOR="#808080"]user:password[/COLOR] "https://mail.google.com/mail/feed/atom" | perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1545    0  1545    0     0   1095      0 --:--:--  0:00:01 --:--:--  1095
	Gmail - Inbox for [COLOR="#808080"]user[/COLOR]@gmail.com</title><tagline>New messages in your Gmail Inbox</tagline><fullcount>2</fullcount><link rel="alternate" href="http://mail.google.com/mail" type="text/html" /><modified>2014-09-29T02:35:29Z</modified><entry><title>Reply to thread 'gmail perl script no longer works.'</title><summary>Dear CantankRus, This is a notification email. PLEASE DO NOT REPLY TO IT. tgalati4 has just replied</summary><link rel="alternate" href="http://mail.google.com/mail?account_id=[COLOR="#808080"]user[/COLOR]@gmail.com&amp;message_id=148be85043165b13&amp;view=conv&amp;extsrc=atom" type="text/html" /><modified>2014-09-28T23:07:41Z</modified><issued>2014-09-28T23:07:41Z</issued><id>tag:gmail.google.com,2004:1480532333941906195</id><author><name>Ubuntu Forums</name><email>info@ubuntuforums.org</email></author></entry><entry><title>Reply to thread '[ubuntu] Cool animated boot splash screen like Ubuntu Kylin'
```


I preferred the perl script's output but I'll just have to use the 
python script which sort of gives me what I want in conky.

---

### Post by vasa1 on 2014-09-28
@CantankRus,
if you have time please explain this part:```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1545    0  1545    0     0   1095      0 --:--:--  0:00:01 --:--:--  1095
```What did you do to get that information? Is it because you aren't using "--silent"?

---

### Post by vasa1 on 2014-09-28
BTW, this also works for me```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-

import sys, imaplib

port = 993
server = 'imap.gmail.com'

username = 'username@gmail.com'
passwd = 'whatever'

imap_server = imaplib.IMAP4_SSL(server, port)
try:
    imap_server.login(username, passwd)
except:
    print('??')
    sys.exit( 1 )

typ, data = imap_server.select ('Inbox', True)
if typ == 'OK':
    total = int(data[0])
    typ, data = imap_server.search (None, 'SEEN')
    if typ == 'OK':
        seen = len(data[0].split())
        print('{}'.format(total - seen))

if typ != 'OK':
    print('??')

imap_server.logout()

# from http://dontsurfinthenude.blogspot.dk/2013/02/check-gmail-script-for-conky-on.html

```in my conky script. I test three gmail accounts like this:
```
${color 555555}${execpi 360 python ~/bin/gm1.py}/${execpi 3600 python ~/bin/gm2.py}/${execpi 300 python ~/bin/gm3.py}/$color
```However, a couple of days ago, this just stopped working and I couldn't figure why. And I couldn't kill conky using pkill which normally works or even by logging out and back in. There were no zombies showing in top's output. Too *Twilight Zone* for me even though I got it working again, I'm now looking at other terminal-based options.

---

### Post by CantankRus on 2014-09-28
Yes that's the info you see when not using **--silent**.

---

