---
title: "Saving the first 4 items of a feed to a file"
date: 2009-04-19
forum: Programming Talk
---

### Post by blairm on 2009-04-19
Hi,

Written a script that downloads an rss feed and sends it by email, but the feed has 20 items in it; I only want the top four. Is there a way to do that in python?
The initial download looks like this:

"http://www.stuff.co.nz/national/2344448/Group-charges-in-to-reduce-bag-use" Group charges in to reduce bag use (Pressure from environmentalists helped sway Foodstuffs' decision to charge for plastic bags.)
"http://www.stuff.co.nz/national/2344526/Veitch-found-safe-after-police-search" Veitch found safe after police search (Broadcaster Tony Veitch, who this week pleaded guilty to injuring his former partner, was the subject of a police search today after the alarm was raised that he had gone missing. )...and so on.

Have a section later in the script that inserts a blank line between each item, if that is helpful.
Should I use regular expressions to find the first four newline characters and print the stuff before the fourth newline to a separate file? Or is there an easier way?

Cheers,

Blair

---

### Post by ghostdog74 on 2009-04-19
```

data=open("file").readlines()
for items in data[:4]:
  print ' '.join(items.split()[1:])


```

---

### Post by blairm on 2009-04-19
Thanks for your help... we're most of the way there, I think.
Inserted the snippet in the script but it is giving me the first item only, not the first four.
Have tried changing values in the snippet but it appears to make no difference. Have I put the snippet in the right place? The script is as follows:

Cheers,

Blair

```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom
import hashlib
import os
import re
#import time


#The url of the feed
address = 'http://www.stuff.co.nz/rss/'

#Our actual xml document
f = open('appendtest.txt.tmp',  'w')

print>>f,  "STUFF TOP STORIES"
document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data

data=open("appendtest.txt.tmp").readlines()
for items in data[:8]:
  print ' '.join(items.split()[1:])
  
print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))
 


    #The url of the feed
addresstwo = 'http://www.stuff.co.nz/rss/national'
#Our actual xml document
f = open('appendtest.txt.tmp',  'a')
print>>f, "<b>STUFF NATIONAL STORIES<b>"
document = xml.dom.minidom.parse(urllib.urlopen(addresstwo))

for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))

 

f.close()

fh = open('appendtest.txt.tmp','r')
stuff = fh.read()
fh.close()

new_stuff = re.sub(r'\)', r')\n\n',stuff)
fh = open('appendtest.txt.tmp','w')
fh.write(new_stuff)
fh.close()

import md5
orig_md5= hashlib.md5(file('newstuff.txt').read())
new_md5= hashlib.md5(file('appendtest.txt.tmp').read())
if orig_md5.digest() == new_md5.digest():
    os.remove('appendtest.txt.tmp')
    sys.exit()
else:
    os.rename('appendtest.txt.tmp',  'newstuff.txt')

import smtplib

 #from http://stackoverflow.com/questions/399129/failing-to-send-email-with-the-python-example
FROMADDR = "orpheus.alert@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "newsalerts"
TOADDRS  = ["blair.mayston@xtra.co.nz",  "blair.mayston@odt.co.nz"]
SUBJECT  = "Stuff rss order test"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += open('newstuff.txt', 'r').read()

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()
```

---

### Post by ghostdog74 on 2009-04-19
if you read a file using readlines() and put to variable, the first 4 lines of the file will be from index 0 to 3
```

open("file").readlines()[:4]

```
following this approach, its easy to test out whether you have got your first 4 items. use the Python shell to do it step by step and look at the result as loop through the for loop.

---

### Post by blairm on 2009-04-20
I'm feeling pretty stupid, but I can't seem to get this working.

Reading the relevant section of the Python documentation and some web posts on the topic I can see that readlines is the command to be using (Reads until EOF using readline() and return a list containing the lines thus read).
By playing in the shell with another file containing similar data have found open("appendtest.txt").readlines()[:16] returns four stories, but when I transfer that to the script the script finds the four stories and will go no further - it won't continue to send an email as it's meant to.

Can anyone explain why? I'm not looking for code to fix the problem, and I'm more than happy to do the work so I can find a solution.
I normally find that I learn things best by throwing myself in the deep end and struggling to stay afloat, but have to say I'm starting to wonder whether programming is an exception to the rule.

Blair

---

### Post by ghostdog74 on 2009-04-20
show how appendtest.txt looks like, and then show how you want your output to be.

---

### Post by blairm on 2009-04-20
Thanks for your patience in helping me.

Have included below a section of appendtest.txt. 
The Stuff Top Stories section only contains one story since I tried to include the snippet posted earlier in the script; it would usually look the same as the Stuff national stories section. 
What I want is to pick up the first four stories in each of the feeds, so in the case of the Stuff national stories it would return Top prize for letting out goo, Teen driver had no licence, Mt Albert byelection date announced and the Phillip Field trial.
Those four items would be written to a file, which would be emailed using smtplib. Don't need any other formatting changes; the format it returns the stories in now (link-headline-first sentence) is fine.
I want to do that with both feeds: I'm assuming what works for the first will also work for the second.

Thanks,

Blair

STUFF TOP STORIES
"http://www.stuff.co.nz/national/2345075/Tony-Veitchs-suicide-bid" Tony Veitch's suicide bid (Just two hours before police took Tony Veitch back to Hamilton's central police station for treatment yesterday after his latest suicide bid, the shamed broadcaster sent a desperate text message to Sunday News.)


<b>STUFF NATIONAL STORIES<b>
"http://www.stuff.co.nz/national/2347463/Top-prize-for-letting-out-goo" Top prize for letting out goo (A chainsaw-wielding creme egg from Feilding has taken the goo.  )


"http://www.stuff.co.nz/national/crime/2347115/Teen-driver-had-no-licence" Teen driver had no licence (A teenage driver who crashed a stolen car into a tree after he sped away from a police cordon early today had no licence, police say.)


"http://www.stuff.co.nz/national/politics/2348237/Mt-Albert-by-election-date-announced" Mt Albert by-election date announced  (A by-election in the Mt Albert electorate to fill the seat left vacant by former prime minister Helen Clark's resignation from Parliament will be held on June 13, Prime Minister John Key announced today.)


"http://www.stuff.co.nz/national/politics/2346351/Phillip-Field-trial-begins" Phillip Field trial begins (A jury has been empanelled for the trial of former MP Taito Phillip Field on 35 criminal charges. )


"http://www.stuff.co.nz/national/crime/2348212/Taxi-driver-accused-also-worked-as-manager" Taxi driver accused also worked as manager (A moonlighting taxi driver accused of exposing himself to a female passenger, then abducting and indecently assaulting her, appeared in Wellington District Court today.)


"http://www.stuff.co.nz/national/crime/2348211/Police-hunt-stabbing-suspect" Police hunt stabbing suspect (Christchurch police are hunting a 25-year-old man suspected of stabbing another man four times in the neck yesterday.)


"http://www.stuff.co.nz/national/crime/2347843/Suppression-continues-for-murder-accused" Suppression continues for murder accused  (The woman charged with the murder of three-year-old Cherish Tahuri-Wright has kept her name suppression today.  )


"http://www.stuff.co.nz/national/crime/2347394/Bain-trial-Bloodied-sockprint-evidence" Bain trial: Bloodied sockprint evidence (Questions from the Bain trial judge have thrown new light on footprint evidence in the High Court retrial in Christchurch.)


"http://www.stuff.co.nz/national/2348147/Air-Force-to-search-for-yacht" Air Force to search for yacht (A Royal New Zealand Air Force Orion and a cargo ship are racing toward a 13 metre Australian yacht with three people on board after it activated a distress beacon.)

---

### Post by ghostdog74 on 2009-04-20
```

data = open("file").readlines()
data = [ i.strip() for i in data] #strip newlines
data = [ i for i in data if i !='' ] #get rid of blank items
for n,l in enumerate(data):
    if "<b>" in l:
        for item in data[n+1:n+1+4]:
            print ' '.join(item.split()[1:])


```
output:
```

# ./test.py
Top prize for letting out goo (A chainsaw-wielding creme egg from Feilding has taken the goo. )
Teen driver had no licence (A teenage driver who crashed a stolen car into a tree after he sped away from a police cordon early today had no licence, police say.)
Mt Albert by-election date announced (A by-election in the Mt Albert electorate to fill the seat left vacant by former prime minister Helen Clark's resignation from Parliament will be held on June 13, Prime Minister John Key announced today.)
Phillip Field trial begins (A jury has been empanelled for the trial of former MP Taito Phillip Field on 35 criminal charges. )


```

---

### Post by blairm on 2009-04-20
Still isn't working for me, so might think about taking a break; have been trying to get this done all day and my head is pounding from all the time at the screen.
Thanks for your help, Ghostdog: you've introduced me to some ideas I hadn't seen in the few weeks I've been playing with Python, so in that sense it's been a successful day.

Blair

---

