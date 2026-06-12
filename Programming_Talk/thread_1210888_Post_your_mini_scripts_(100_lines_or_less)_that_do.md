---
title: "Post your mini scripts (100 lines or less) that do nifty things"
date: 2009-07-12
forum: Programming Talk
---

### Post by Warren Watts on 2009-07-12
As an amateur programmer, I get bored sometimes and set out to write little scripts (Usually in perl, but more and more in PHP lately) that teach me something new and do something useful.

Here's a perl script  I wrote that retrieves and displays a random quote from [www.quotationspage.com](www.quotationspage.com) .  I wrote it to show me a random quote every time I log in to my server via SSH.

Anyone else got any nifty little "scriptlets" they want to share?

[PHP]#!/usr/bin/perl

######################################################################################
# random_quote.pl version 0.91 7/11/09
# Author: Warren Watts (kingbeetle_66(at)yahoo(dot)com
# When executed from the command line, this program will retrieve and display random
# quotes from www.quotationspage.com.

# The number of quotes to be displayed can be specified at the command line.
# For example, entering "perl random_quote.pl 3" would display three quotes.
# Up to fifteen quotes can be displayed.
# Copyright 2007,2009 Warren B. Watts

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#######################################################################################

use strict;

my ($quote_count,$return_count,$user_agent,$response,@forms,@checkbox_values,@form_out,$form,@inputs,$inp);
my ($type,$value,$check_value,$name,$page,$display_count,$quote,$quote_string,$author);

use HTML::Form;
use LWP::UserAgent;

if (@ARGV) {$quote_count = $ARGV[0]}         # If a number is passed as a command line parameter, store it in $quote_count
else {$quote_count = 1}                      # Otherwise, set $quote_count to 1
$return_count = $quote_count;                # Store $quote_count in $return_count
if ($quote_count < 4) {$return_count = 4}    # Limit $return_count to the range of (4..15)
if ($quote_count > 15) {$return_count = 15}

$user_agent = LWP::UserAgent->new;
$response = $user_agent->get("http://www.quotationspage.com/random.php3"); # Retrieve the form from the webpage
@forms = HTML::Form->parse($response); # Store the form in a HTML::Form hash

# Store the form's checkbox names in an array
@checkbox_values = ("mgm","motivate","classic","coles","lindsly","poorc","altq","20thcent","bywomen","devils","contrib");

undef(@form_out);  # Clear the array that the modified form will be "pushed" into
  $form = shift(@forms); # There are two forms on the website; We are only interested in the second form, so toss out the first hash
  $form = shift(@forms); # Pull out the second form
  @inputs = $form->inputs; # Store the hash into an array
  for (my $i=0 ; $i<=$#inputs ; $i++)
  {
    $inp = $inputs[$i];
    $type = $inp->type;
   if ($type eq "option") # If the form element is the quote count, stamp in the requested number of quotes
   {
     $inp->value($return_count);
   }
   if ($type eq "checkbox") # If the form element is a checkbox, stamp in the next checkbox name from the @checkbox_values array
    {
      $check_value = shift(@checkbox_values);
      $inp->value($check_value);
    }
    $value = $inp->value;
    $name = $inp->name;

    # As long as the form element isn't submit, push the form element into the output form array
     if ($type ne "submit") {push(@form_out,$name,$value)}
 }
$response = $user_agent->post('http://www.quotationspage.com/random.php3',\@form_out); # Post the completed form the the website and retieve the HTML
$page = $response->as_string;

$display_count = 0;
while ($page =~ m/<dt class=\"quote\">(.*?)<\/dd>/gs) # Look for a quote in the HTML
{
  $quote = $1;
  if ($quote =~ m/\.html">(.*?)<\/a>/) # Extract the quote
  {
    $quote_string = $1;
    $quote_string =~ s/<br> /\n/gs; # Replace any HTML <br> statements with Newlines
  }
  if ($quote =~ m/<b>(.*?)<\/b>/) # Extract the author
  {
    $author = $1;
    if ($author =~ m/\/">(.*?)$/) # If the author is imbedded in a link, remove the link HTML
    {
      $author = $1;
      $author =~ s/<\/a>//;
    }
    $display_count++;

    # Since the webpage always returns a minimum of four quotes,
    # limit the number of quotes displayed to the number of quotes specified at the command line.
    if ($display_count <= $quote_count) {print $quote_string." - ".$author."\n\n"}
  }
}


[/PHP]

---

### Post by JohnnySage50307 on 2009-07-12
import random
size = 1024
for i in range(size):
 print random.randint(0,256),
 
[FONT=Times New Roman][SIZE=2]Using this, you can redirect the output into a file and just fill up a file of the specified size.  Pretty good if you want to pad some data or if you have a psychotic teacher who wants you to code an interface to send out exactly Xk bytes of data.[/SIZE][/FONT]

---

### Post by wmcbrine on 2009-07-12
A program to report the width and height of a TV, in both 4:3 and 16:9 shapes, given only the diagonal (the usual advertised figure). I did this to make it easier to figure out what size of 16:9 TV would be needed to replace a 4:3 TV while keeping the same screen height. But mainly I wrote it because I was bored and in a situation where I couldn't do much else at the time.

tvarea.py:
```
#!/usr/bin/env python

import math
import sys

_16X9_DIAG_BASE = math.sqrt(337)

def show(shape, width, height):
    print ('%4s set: width %5.2f x height %5.2f = %6.2f sq. in.' %
           (shape, width, height, width * height))

def both_from_diag(diag):
    base = diag / _16X9_DIAG_BASE
    show('16:9', base * 16, base * 9)

    base = diag / 5.0
    show('4:3', base * 4, base * 3)

if len(sys.argv) > 1:
    for arg in sys.argv[1:]:
        print 'Diagonal:', arg
        both_from_diag(int(arg))
else:
    both_from_diag(input('Diagonal? '))
```

---

### Post by wmcbrine on 2009-07-12
> **JohnnySage50307 said:**
> Pretty good if you want to pad some data or if you have a psychotic teacher who wants you to code an interface to send out exactly Xk bytes of data.It doesn't do that, you know. You're just printing the number, so it can range from 1-3 bytes each time (1024-3072 bytes for the whole thing). I think you want a chr() around your random.randint()... although then you run into the issue that only 0-127 are ASCII, so Python may complain about 128-255.

---

### Post by Warren Watts on 2009-07-12
> **wmcbrine said:**
> But mainly I wrote it because I was bored and in a situation where I couldn't do much else at the time..

Cool!  Exactly the kind of code I was hoping people would post;  perhaps not something that is universally useful to a wide audience, but something that met a specific need, was fun to write, and was primarily written because you were bored and wanted to learn how to do something new.

I really hope this thread takes off!

---

### Post by jimi_hendrix on 2009-07-12
> **wmcbrine said:**
> It doesn't do that, you know. You're just printing the number, so it can range from 1-3 bytes each time (1024-3072 bytes for the whole thing). I think you want a chr() around your random.randint()... although then you run into the issue that only 0-127 are ASCII, so Python may complain about 128-255.

unichr

---

### Post by wmcbrine on 2009-07-12
> **jimi_hendrix said:**
> unichrWould not help. The problem comes when he prints it.

---

### Post by Warren Watts on 2009-07-15
I hate to see this thread die, so here is another nifty little perl script I wrote:


I was reading an Ubuntu Forum thread about tweaking the speed of your internet connection in Linux, and there was a post about using dig to test the DNS servers listed in the /etc/resolv.conf file.

I expanded the idea by writing a perl script that reads the /etc/resolv.conf file and tests each DNS server at several different domains worldwide and sorts the results fastest to slowest.

I recently added a feature that allows command line passing of additional DNS servers to be tested.

[PHP]

#!/usr/bin/perl

######################################################################################
# scan_dns.pl version 0.8 7/14/09
# Author: Warren Watts (kingbeetle_66(at)yahoo(dot)com

# This program will analyze the relative speeds of each of the DNS servers
# detected by dhcpcd (DHCP client daemon) through use of dig (a DNS lookup utility)
# and display a sorted list of DNS servers from fastest to slowest.
# This sorted list can then be used to tweak the /etc/resolv.conf file, providing
# faster DNS lookups while browsing, etc.

# I included three domains for dig to lookup.  They are stored in @domain_list.
# Feel free to add to the list or change the domain list to any domains you wish.
# You can also pass edditional DNS servers to be tested to the script at the command line:
# EXAMPLE: perl scan_dns.pl 192.168.1.234 70.82.32.232
# Be aware that the more domains in the list, the longer the scan will take!

# Copyright 2007,2009 Warren B. Watts
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#######################################################################################

use strict;

my (@DNS,$parm,$bad_format,$IP,$time,$domain,$dig,%time,$key);

# Read the DNS list from /etc/resolv.conf and store the list in an array
my $resolv = `cat /etc/resolv.conf`;
while ($resolv =~ /nameserver (.*)\n/g) {push(@DNS,$1)}

# Check for additional DNS servers to be tested that might have been entered at the command line
# and add them to the array of servers to be tested
if (@ARGV)
{
  # if the DNS server address has a valid format, and all the octets are within range, add the DNS server
  # to the array of servers to be tested, otherwise display an error
  foreach $parm (@ARGV)
  {
    undef($bad_format);
    if ($parm =~ m/^(\d\d?\d?)\.(\d\d?\d?)\.(\d\d?\d?)\.(\d\d?\d?)/ )
    {
      if($1 <= 255 && $2 <= 255 && $3 <= 255 && $4 <= 255) {push(@DNS,$parm)}
      else {$bad_format = 1}
    }
    else {$bad_format = 1}

    if ($bad_format)
    {
      print "\n+---------------------------------- ERROR --------------------------------+\n";
      print("DNS server $parm is not in a valid format and will not be tested.\n");
      print "+---------------------------------- ERROR --------------------------------+\n";
    }
  }
}

#List the DNS servers to be tested
print "\n+-------------------------------------------------------------------------+\n";
print "The following DNS servers will be tested:\n";
foreach $IP (@DNS) {print "$IP\t"}
print "\n";

# Store list of domains to be looked up by dig in an array
my @domain_list = ('www.yahoo.com' ,'www.fasthit.net' ,'zz.nullwave.ru');

# List the domains to be used by dig during the scan
print "The following domains will be tested in this scan:\n";
foreach $domain (@domain_list) {print "$domain\t"}
print "\n";
print "+-------------------------------------------------------------------------+\n";

# Count number of domains stored in the array
my $domain_count = @domain_list;
# Go through the list of DNS servers and execute dig for each DNS server and each
# domains in the domain list, extract the time taken and average the times together,
# then store the DNS and averaged time in a hash.
foreach $IP (@DNS)
{
  print "Scanning $IP\n";
  $time = '';
  foreach $domain (@domain_list)
  {
    print "-->  $domain\n";
    $dig = `dig \@$IP $domain`;
    if ($dig =~ /Query time: (.*) msec/)
    {
      $time = $time + $1;
    }
  }
  $time{$IP} = int(($time / $domain_count) +0.5);
}
print "+-------------------------------------------------------------------------+\n";

# Display the results sorted by time in ascending order
foreach my $key (sort hashValueAscendingNum (keys(%time)))
{
  print "Average fetch time for $key : $time{$key} msec\n";
}
print "\n";
# Subroutine to sort by time rather than by DNS address
sub hashValueAscendingNum
{
   $time{$a} <=> $time{$b}
}
[/PHP]

BTW, I know it's over 100 lines, but it would be tiny of you took out all the comments!

---

### Post by Can+~ on 2009-07-15
[PHP]#!/usr/bin/env python

import webbrowser, os

open("hello.html", "w").write("<html><head><title>Why so serious?</title></head>\n<body><img src='http://www.viralchart.ru/Images1/Images/serious_cat/15.jpg'</body></html>")

webbrowser.open_new_tab("file://"+os.getcwd()+"/hello.html")[/PHP]

3 working lines. Make sure that Firefox/Opera/Chromium/Whichever-that-can-render-html is the default opener for .html.

---

### Post by master_kernel on 2009-07-15
Finds all ssh-communicable computers on a given network. (port 22)

[PHP]#!/usr/bin/env python

import os
import socket, sys
from optparse import OptionParser 

def getMyIP():
    from socket import socket, SOCK_DGRAM, AF_INET
    s = socket(AF_INET, SOCK_DGRAM)
    s.connect(('google.com', 0))
    return s.getsockname()[0]

def scan_server(address):
    socket.setdefaulttimeout(5)
    s = socket.socket()
    #print "Attempting to connect to %s on port %s." %(address, port)
    try:
        s.connect((address, 22))
        #print "Connected to server %s on port %s." %(address, port)
        return True
    except socket.error, e:
        #print "Connecting to %s on port %s failed with the following error: %s" %(address, port, e)
        return e

badlist = []
list = []
print "\nYour IP address: " + getMyIP()
print "Scanning network, please wait..."
# Check 192.168.2.3 - 192.168.2.9
for i in range(3,10):
    ip_address = "192.168.2." + str(i)
    check = scan_server(ip_address)
    if check == True:
        list.append(ip_address)
    else:
        ip_address = ip_address + ": " + str(check)
        badlist.append(ip_address)
print
print "SSH addresses\n============="
for i in list:
    print i

print
print "Error list:\n=========="

for i in badlist:
    print i

print
sys.exit(0)[/PHP]

---

### Post by wmcbrine on 2009-07-15
I have a lot of little one-off programs, but most of them are in C, so technically not "scripts".

---

### Post by Warren Watts on 2009-07-15
> **wmcbrine said:**
> I have a lot of little one-off programs, but most of them are in C, so technically not "scripts".

I didn't really intend posts to this thread to be limited to purely scripts.  Perhaps my use of the word scripts in the title was a bit of a [misnomer]("http://www.merriam-webster.com/dictionary/misnomer").

Feel free to post code in whatever language you use!

---

### Post by c0mput3r_n3rD on 2009-07-15
It's nothing amazing, but if you live in a house full people like me, it's nice to be able to walk away from your computer and know no one can mess with it:
```

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# # Title: lock                                                     # # 
# # Original Author: Matthew Van Helden                             # #
# # Date last modified: June 17, 2009                               # #
# # Copyright: None. Open source. (Must keep origianl authtors name)# #
# # Description: Takes one argument, and uses that as the code to   # #
# #         unlock the computer.  After 3 wrong attempts, (as   # #
# #        though some one else is trying to get on your       # #
# #        computer) your linux box will reboot.  How ever,    # #
# #        because you have a sudo command, you must log in    # #
# #        as root before running the programming:             # #
# #                            sudo su     # #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #        

if [ "$#" != 1 ]
  then
    echo "Usage: $0 [argument]"
    exit 1
fi
if [ -f wrong_attempts.txt ]
  then
    rm wrong_attempts.txt
  fi
clear
trap '' 1 2 5 10 15 20
stty -echo
code="$1"
echo "                                                                         COMPUTER IS LOCKED!!!"
echo "                                                                        ------------------------"
echo
echo -n "Enter code to unlock: "
read code2
if [ $code2 != $1 ]
  then
    echo $code2 >> wrong_attempts.txt
  fi
echo
wrong=1
while [ "$code" != "$code2" ]
  do
    echo 
    echo "--ERROR--"
    echo 
    echo -n "Enter code to unlock: "
    read code2
    if [ $code2 != $1 ]
      then
        wrong=$((wrong+1))
        echo $code2 >> wrong_attempts.txt
      fi
    if [ $wrong == 3 ]
      then
        clear
        echo
        echo "      3 WRONG ENTRIES WILL NOW TERMINATE THIS SESSION..."
        echo
        shutdown -r now
      fi
    echo
  done
clear
echo
echo "                                                                         COMPUTER IS UNLOCKED!!!"
echo "                                                                        --------------------------"
echo
stty echo
echo "You are here: ${PWD}"

```

---

### Post by Reiger on 2009-07-15
I find the last entry a bit curious. I mean pulling out 3-wrong-attempts and thereby force reboot is as good as any way for someone to kick your session out and start their own?

---

### Post by c0mput3r_n3rD on 2009-07-15
> **Reiger said:**
> I find the last entry a bit curious. I mean pulling out 3-wrong-attempts and thereby force reboot is as good as any way for someone to kick your session out and start their own?

Well the reason why I do it is because you wont be able to sign back in on my computer #1, you wont be able to get at my files #2, and there's no way to hid the fact that some tried to get into the computer.  It works to my liking, and like I said, it's not special but it gets the job done for me, and that's all that really matters :D

---

### Post by JordyD on 2009-07-15
I assume you only use this for non-X sessions, yes?

---

### Post by keplerspeed on 2009-07-15
Bash script to set the astronomy picture of the day as the wallpaper.

```

#!/bin/bash

#change this if you want the image to be in a different directory
FILENAME=apodwallpaper
APODWALLPAPER=${HOME}/.${FILENAME}

mkdir -p ${APODWALLPAPER} && cd ${APODWALLPAPER}

# download image from apod site
wget -A.jpg -R.txt -r -l1 --no-parent -nH http://antwrp.gsfc.nasa.gov/apod/astropix.html

# move image from obscure folder to main folder, rename image
find ./apod -name "*.jpg" | while read line ; do
mv "$line" "${FILENAME}.jpg"
done

# set image to wallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "blank.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "${APODWALLPAPER}/${FILENAME}.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_options "scaled"

#get rid of cruft
rm -rf apod robots.txt


```

---

### Post by keplerspeed on 2009-07-15
Bash script to turn on or off the xwinwrap wallpaper.

```

#!/bin/bash

# This script runs xwinwrap

# If glmatrix is running kill it 
if pidof glmatrix 
    then pkill glmatrix 
else

# move to the xwinwrap directory 
cd /usr/local/xwinwrap/ 

# execute xwinwrap with required arguements 
./xwinwrap -ni -argb -fs -s -st -sp -nf -b -o 0.7 -- /usr/lib/xscreensaver/glmatrix -window-id WID fi 

```

---

### Post by chronographer on 2009-07-15
I am pretty happy with this script. It uses python, and talks to my ISP's API for sending text messages (SMS) to randomise a set of names and mobile numbers and to assign each person a different person for Chris Cringle (you know like secret santa, where each member of my family only gets one present for another person).

Here it is: 
```
#!/usr/bin/python

#########################
import urllib,random
from copy import deepcopy
print "************************"
print "SMS secret santa starts!"
print "************************\n"

#CUSTOM SETTINGS HERE:
USERNAME = ********
PASSWORD = ********
MYMOBILE = 'KrisKringle'
toNum = '********'
dictionary = {'Todd':'********','Alex':'********','Rani':'********',\
'Simone':'********','Anne':'********','Alana':'********',\
'Aaron':'********','Neil':'********','Anna':'********'}
names = dictionary.keys()
worked = 0
namesAssigned = []

#Send one message (can be used many times).
def OnSend(to,mess,fm='********'):
        fm = urllib.quote(fm)
        to = urllib.quote(to)
        mess = urllib.quote(mess)
        text =  """https://www.********.com.au/sendsms/api_sms.php?username=%s&password=%s&mobilenumber=%s&message=%s&sender=%s&messagetype=Text"""\
        %( USERNAME, PASSWORD , to , mess , fm)
        returned = urllib.urlopen(text)
        s = returned.read()
        returned.close()
        s = urllib.unquote(s)
        split = s.split('|')
        status = split[4]
        if 'OK' in status:
            print 'Message sent, status was: OK'
        else:
            print "WARNING: failed"
            print 'The status was: ',status

#Assign names, careful that no one gets themselves
def Assign(na):
    naR = deepcopy(na)
    random.shuffle(naR)
    for i,n in enumerate(na):
        while na[i] == naR[-1]:
            if len(naR) == 1:
                print "last names match... need to run again."
                return 0
            print "double found, reshuffling"
            random.shuffle(naR)
        namesAssigned.append(naR[-1])
        naR.pop()
    return 1
        
#mix the names up! This loops until a satisfactory solution is found.   
while worked != 1:
    print "shuffling the names around..."
    naR=[]
    na=[]
    namesAssigned = []
    worked = Assign(names)
print "finished shuffling\n"

#send messages
def Send():
    for n,i in enumerate(names):
        print "Sending message to %s on: %s" \
        %(i,dictionary[i])
        text = """Merry Christmas %s! This is Secret Santa. You are to please get a gift for %s. This has been randomly generated, don't lose it!""" %(i,namesAssigned[n])
        #OnSend uses (TO, Message, From)
        OnSend(dictionary[i],text,MYMOBILE)

###############################################
#Uncommenting this bit will actually send the messages.
Send()
###############################################

try:
    print "\nlog written"
    log = open("/home/alex/.kriskringle.txt",'w')
    for i in range(len(names)):
        logtext = "%s got %s\n" %(names[i],namesAssigned[i])
        log.write(logtext)
finally:
    log.close()
    
print "\n************************"
print "Secret Santa ends."
print "************************\n"
```

p.s. don't tell any of my family that I did save a secret list of the present pairs as they think no-body knows who gets who!!!! What do you think?

---

### Post by soltanis on 2009-07-16
Kill processes unconditionally:

```

ps -e | grep <name> | awk '{print $1;}' | xargs kill -9

```

---

### Post by Warren Watts on 2009-07-16
> **chronographer said:**
> What do you think?

Gotta make all your expensive hardware do **something** useful every once and a while!

Who needs scraps of paper and a hat, when you have Python? :lolflag:

---

### Post by J V on 2009-10-11
thread is dead? Well I need a little script that can dump some variables to a file and load them back up again, nice for saving settings etc... Will post later :)

---

### Post by ApEkV2 on 2009-10-11
Search a directory full of source code, and display which file and line had a match.
This helps a lot when it comes to finding things in a large program's source code. 
```
#!/bin/bash

read -p "Enter the target directory to search:" zTarget
read -p "Would you like to start the script [Y/N]:" zStart
if [ -z $zStart ] || [[ $zStart == [nN]* ]]; then
 echo "Exit 0"
 exit 0; fi
find $zTarget -type f -name '*.c' | while read zIn; do
	zOut=`grep -n -H 'PATTERN' $zIn`
	echo "$zOut"; done
```

---

### Post by maximinus_uk on 2009-10-11
More of a one-liner than a script, displays most used commands in bash:

```
#!/bin/bash

echo "Top ten most used commands:"
cat ~/.bash_history | awk '{print $1}' | sort | uniq -c | sort -nr | head -10
```

---

### Post by TiredBird on 2009-10-12
This script creates a mount point, provides a way to know whether or not a mount has taken place and assigns a specified owner and group.

The script takes five arguments: (1) path on which to make the mount; (2) the name of the mount point; (3) the name of the zero length file to be created in the mount point (when accessible indicates that a mount has not taken place); (4) owner name for the mount point; and (5) group name for the mount point.

I generally invoke this script from other scripts that need known mount points such as udev or Truecrypt scripts that need to mount a dataset at a known point.

---

### Post by Can+~ on 2009-10-12
Python:
[PHP]compose = lambda *funcs: reduce(lambda f, g: lambda *args, **kaargs: f(g(*args, **kaargs)), funcs)[/PHP]

A compositional function that combines n functions into a single one, like:

```
compose(f, g, h) = (f o g o h)
```

Example:
[PHP]f = lambda x: x+1
g = lambda x: x*2
h = lambda x: x-3

# x=10 : ((x-3)*2)+1 = 15
print (compose(f, g, h))(10)[/PHP]

---

### Post by Can+~ on 2009-10-12
On a side note, I just discovered this:

[http://arctrix.com/nas/python/bpnn.py](http://arctrix.com/nas/python/bpnn.py)

A neural network coded under 200 lines (remove comments, demo, and other stuff and you could get < 100).

---

### Post by NoaHall on 2009-10-12
```

#! /bin/bash
next=0
function one
{
    echo "What number/program name do you want to get?"
    read progdown
}
function two
{
    if [ $progdown == "q" ]; then
        exit
    elif [ $progdown == "r" ]; then
        echo "Reloading"
        get_iplayer -f | grep $prog
        one
    else
		three
    fi
}
function three
{
	while [ $next != 1 ];
	do
		
		get_iplayer --get $progdown &&
		notify-send "Iplayer Download has finished"
		let next=1
		two
	done
}
function four 
{
	if [ $prog = "1" ]; then
		six
	else 
		five
	fi
}
function five
{
get_iplayer -f | grep $prog
one
two
}
function six 
{
get_iplayer -f | grep //***insert a program you want to add a shortcut to here***\\
one
two
}
echo "What program do you want to search for?"
read prog
four

```

A script to work with get_iplayer for a nicer terminal interface.

---

### Post by Siph0n on 2009-10-12
I wrote this one to find the differences in two files (two lists of employee ids) for work.

```
# Shawn McCarthy's Difference in two files
# 2007-11-21

readFile1=open('read1.txt', 'r')
readFile2=open('read2.txt', 'r')
writeFile=open('difference.txt', 'w')

readList1 = []
readList2 = []

# Create list from file 1
for line in readFile1:
    readList1.append(line.strip('\n'))

# Create list from file 2
for line in readFile2:
    readList2.append(line.strip('\n'))

readFile1.close()
readFile2.close()

writeFile.write('File 1 has these, but File 2 does not:\n')
for line in readList1:
    if line not in readList2:
        writeFile.write(line)
        writeFile.write('\n')

writeFile.write('\n')

writeFile.write('File 2 has these, but File 1 does not:\n')
for line in readList2:
    if line not in readList1:
        writeFile.write(line)
        writeFile.write('\n')

writeFile.close()
```

---

### Post by eightmillion on 2009-10-12
> **Siph0n said:**
> I wrote this one to find the differences in two files (two lists of employee ids) for work.

```
# Shawn McCarthy's Difference in two files
# 2007-11-21

readFile1=open('read1.txt', 'r')
readFile2=open('read2.txt', 'r')
writeFile=open('difference.txt', 'w')

readList1 = []
readList2 = []

# Create list from file 1
for line in readFile1:
    readList1.append(line.strip('\n'))

# Create list from file 2
for line in readFile2:
    readList2.append(line.strip('\n'))

readFile1.close()
readFile2.close()

writeFile.write('File 1 has these, but File 2 does not:\n')
for line in readList1:
    if line not in readList2:
        writeFile.write(line)
        writeFile.write('\n')

writeFile.write('\n')

writeFile.write('File 2 has these, but File 1 does not:\n')
for line in readList2:
    if line not in readList1:
        writeFile.write(line)
        writeFile.write('\n')

writeFile.close()
```

Just for fun/challenge, I tried to compact this code as much as possible. This is what I ended up with.

[PHP]a,b,x,y=open('read1.txt').readlines(),open('read2.txt').readlines(),'File %d has these, but File %d does not:\n',lambda a,b:filter(lambda x:x not in a,b);open('difference.txt','w').writelines([x%(1,2)]+y(b,a)+["\n"+x%(2,1)]+y(a,b))[/PHP]

---

### Post by NoaHall on 2009-10-12
That's really disgusting :D Why not do it on multiple lines? Being on one single line doesn't do much.

---

### Post by eightmillion on 2009-10-12
> **NoaHall said:**
> That's really disgusting :D Why not do it on multiple lines? Being on one single line doesn't do much.

It's just for fun. It really doesn't serve any useful purpose other than to entertain me. :)

---

### Post by diesch on 2009-10-12
Download the classifier list from [PyPI]("http://pypi.python.org/"), displays a list where you can select classifiers and prints the selected classifiers.
          
```
#!/bin/sh

#
# Written by Florian Diesch <devel@florian-diesch.de> 
#
# Updates may be available at
# <http://www.florian-diesch-.de/software/shell-scripts/> 
#
# This script is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  
# You are free to do with it what ever you want.


tmp=$(tempfile --prefix pypicats)


zenity --progress --title 'Please wait' --auto-kill --pulsate \
       --text 'Downloading trove classifiers from PyPI' &

pid=$!
              
wget -q -O - 'http://pypi.python.org/pypi?%3Aaction=list_classifiers' |
xargs  -i -d '\n' printf "FALSE\n{}\n"  > "$tmp"

kill $pid

zenity --title 'Trove Classifiers' --list --checklist --multiple \
       --text 'Select trove classifiers' --column='' \
       --column='Classifier' --separator "$(printf "\n ")"  \
       --height=800 --width=600 < "$tmp"  | \
sed -es"/ *\(.*\)/'\1',/"

rm "$tmp"
```I have some more on [http://www.florian-diesch.de/software/shell-scripts/](http://www.florian-diesch.de/software/shell-scripts/)

---

### Post by eightmillion on 2009-10-12
I suppose I might as well post a small script that I wrote to get translations from google. If a language to translate from isn't provided, then google tries to detect the language. I've found that most of the time it isn't necessary to specify which language you're trying to translate.

It depends on beautifulsoup and simplejson.

[PHP]#!/usr/bin/env python                                                                                                                                                                   
import urllib, os                                                                                                                                                                       
from BeautifulSoup import BeautifulStoneSoup                                                                                                                                            
from simplejson import loads                                                                                                                                                            
from optparse import OptionParser, SUPPRESS_HELP                                                                                                                                        
usage = "Usage: translate -l --list -f --from [language] -t --to [language] [text to be translated]"                                                                                    
Languages = """                                                                                                                                                                         
  AFRIKAANS : af\n  ALBANIAN : sq\n  AMHARIC : am\n  ARABIC : ar\n  ARMENIAN : hy\n  AZERBAIJANI : az\n  BASQUE : eu\n  BELARUSIAN : be\n  BENGALI : bn\n  BIHARI : bh                  
  BULGARIAN : bg\n  BURMESE : my\n  CATALAN : ca\n  CHEROKEE : chr\n  CHINESE : zh\n  CHINESE_SIMPLIFIED : zh-CN\n  CHINESE_TRADITIONAL : zh-TW\n  CROATIAN : hr\n  CZECH : cs          
  DANISH : da\n  DHIVEHI : dv\n  DUTCH : nl  \n  ENGLISH : en\n  ESPERANTO : eo\n  ESTONIAN : et\n  FILIPINO : tl\n  FINNISH : fi\n  FRENCH : fr\n  GALICIAN : gl\n  GEORGIAN : ka      
  GERMAN : de\n  GREEK : el\n  GUARANI : gn\n  GUJARATI : gu\n  HEBREW : iw\n  HINDI : hi\n  HUNGARIAN : hu\n  ICELANDIC : is\n  INDONESIAN : id\n  INUKTITUT : iu\n  ITALIAN : it      
  JAPANESE : ja\n  KANNADA : kn\n  KAZAKH : kk\n  KHMER : km\n  KOREAN : ko\n  KURDISH : ku\n  KYRGYZ : ky\n  LAOTHIAN : lo\n  LATVIAN : lv\n  LITHUANIAN : lt\n  MACEDONIAN : mk       
  MALAY : ms\n  MALAYALAM : ml\n  MALTESE : mt\n  MARATHI : mr\n  MONGOLIAN : mn\n  NEPALI : ne\n  NORWEGIAN : no\n  ORIYA : or\n  PASHTO : ps\n  PERSIAN : fa\n  POLISH : pl           
  PORTUGUESE : pt-PT\n  PUNJABI : pa\n  ROMANIAN : ro\n  RUSSIAN : ru\n  SANSKRIT : sa\n  SERBIAN : sr\n  SINDHI : sd\n  SINHALESE : si\n  SLOVAK : sk\n  SLOVENIAN : sl\n  SPANISH : es
  SWAHILI : sw\n  SWEDISH : sv\n  TAJIK : tg\n  TAMIL : ta\n  TAGALOG : tl\n  TELUGU : te\n  THAI : th\n  TIBETAN : bo\n  TURKISH : tr\n  UKRAINIAN : uk\n  URDU : ur\n  UZBEK : uz     
  UIGHUR : ug\n  VIETNAMESE : vi                                                                                                                                                        
"""                                                                                                                                                                                     
if __name__ == "__main__":                                                                                                                                                              
        parser = OptionParser(usage=usage, version="%prog 0.9.8")                                                                                                                       
        parser.add_option("-f", "--from", dest="fromLang", help="Translate from this language.")                                                                                        
        parser.add_option("-t", "--to", dest="toLang", help="Translate to this language. Default is English.")                                                                          
        parser.add_option("-l", "--list", action="store_true", default=False, dest="listLang", help="Display a list of language codes.")                                                
        parser.add_option("--file", dest="file", help="Translate a file.")                                                                                                              
        (options, args) = parser.parse_args()                                                                                                                                           
        if options.listLang:                                                                                                                                                            
                print Languages
                exit()
        if options.fromLang:
                fromLang = options.fromLang
        else:
                fromLang = ''
        if options.toLang:
                toLang = options.toLang
        else:
                toLang = 'en'
        if options.file:
                if os.path.isfile(options.file):
                        try:
                                transString = urllib.quote(file(options.file).read())
                        except:
                                print "Couldn't open file: %s" % options.file
                                exit()
                else:
                        print "Couldn't open file: %s" % options.file
                        exit()
        else:
                transString = urllib.quote(" ".join(args))
        results = urllib.urlopen('http://ajax.googleapis.com/ajax/services/language/translate?v=1.0&q=' + transString + '&langpair=' + fromLang + '%7C' + toLang).read()
        try:
                if loads(results)["responseData"].has_key("detectedSourceLanguage"):
                        detected = "(detected language: %s)" % loads(results)["responseData"]["detectedSourceLanguage"]
                else: detected = ''
        except:
                 detected = ''
        try:
                print "Translated text %s: " % detected + unicode(BeautifulStoneSoup(loads(results)["responseData"]["translatedText"],convertEntities=BeautifulStoneSoup.HTML_ENTITIES))
        except:
                print "The phrase couldn't be translated."[/PHP]

---

### Post by homerhomer on 2009-10-12
This is a little script that I wrote when I was bored. It cleans up Firefox's database.
It also checks to see if Xorg is running and if so it starts a terminal. You really only need the last 8 lines but the rest of it makes it fun.




#!/bin/bash

# Check is X is running
if [ -n "`pidof X`" ]; then
	if [ "$RUNNING_IN_NEW_XTERM" != t ] ; then
        RUNNING_IN_NEW_XTERM=t exec xterm -e "$0 $*"
	fi
fi

if [ ! -n "`which sqlite3`" ]
then 
	echo "You need to install sqlite3"
read -p ""
exit
fi

ff=`ps axu | grep -i firefox | grep -v grep`

if [ "$ff" != "" ]
then
	read -p  "You need shutdown firefox first!"
exit

fi

echo "Vacuuming Firefox's Sqlite Files"
echo ""
for F in $(find ~/.mozilla/ -type f -name '*.sqlite' -print)
do
sqlite3 $F "VACUUM;"
done
echo ""
read -p "All done"

---

### Post by ghostdog74 on 2009-10-12
> **eightmillion said:**
> Just for fun/challenge, I tried to compact this code as much as possible. This is what I ended up with.

[PHP]a,b,x=open('read1.txt').readlines(),open('read2.txt').readlines(),'File %d has these, but File %d does not:\n';open('difference.txt','w').writelines([x%(1,2)]+filter(lambda x:x not in b,a)+["\n"+x%(2,1)]+filter(lambda x:x not in a,b))[/PHP]

so what's the difference between this and what filecmp module provides?

---

### Post by falconindy on 2009-10-12
For anyone who does the NY times puzzle on a daily basis, add this to your crontab to run at about 10:10pm EST each night. Add in your own login info, of course...
```
#!/bin/bash

usage() {
	echo "Usage: getDailyCrossword.sh [date]"
	echo "   date can be in mm/dd/yy form or a valid token: yesterday|today|tomorrow"
	exit 0
}

case $1 in
  today|tomorrow|yesterday )
	DATESTRING=`date --date=$1 +%b%d%y`
  ;;
  *[[:digit:]]/*[[:digit:]]/*[[:digit:]] )
	DATESTRING=`date --date=$1 +%b%d%y`
  ;;
  *)
	usage
  ;;	
esac

COOKIE_JAR=cookies.tmp
WEB_PAGE=tmp.html
LOGIN_PAGE=http://www.nytimes.com/auth/login
USERNAME="USERID=<username goes here>"
PASSWORD="PASSWORD=<password goes here>"
XWORD_URL="http://select.nytimes.com/premium/xword/$DATESTRING.puz"
HIDDEN_FIELDS="is_continue=true&URI=http://&OQ=&OP=Submit2=Log%20In"
OUTPUT_DIR="$HOME/Desktop"

echo -n "Logging in... "
curl --silent --cookie-jar $COOKIE_JAR \
	--output $WEB_PAGE \
	$LOGIN_PAGE

curl --silent --cookie $COOKIE_JAR --cookie-jar $COOKIE_JAR \
	--data "$HIDDEN_FIELDS&$USERNAME&$PASSWORD" \
	--output $WEB_PAGE \
	--location \
	$LOGIN_PAGE

# Make sure we're logged in
if [[ `cat $COOKIE_JAR | wc -l` -lt 7 ]]; then
	echo "failed!"
	exit 1
else
	echo "success!"
fi

# Get the puzzle
echo -n "Getting puzzle for $1... "
curl --silent --cookie $COOKIE_JAR --cookie-jar $COOKIE_JAR \
	--output $OUTPUT_DIR/$DATESTRING.puz \
	$XWORD_URL

#What type of file is our result?
RESULT=`file $OUTPUT_DIR/$DATESTRING.puz | cut -d\  -f2-`

case "$RESULT" in
  "data")
	echo "success!"
	rm $WEB_PAGE
	rm $COOKIE_JAR
  ;;
  "HTML document text")
	echo "error! (Puzzle not yet available?)"
	if [[ -e $OUTPUT_DIR/$DATESTRING.puz ]]; then
		rm $OUTPUT_DIR/$DATESTRING.puz
	fi
	exit 1
  ;;
esac
```

---

### Post by StunnerAlpha on 2009-10-12
Here is a python script(more of a module) I recently made for a larger program of mine. I made this script to determine what flags were present and what order they are in relative to one another. Hopefully some of you can find this useful. (Sorry its a bit over 100 lines but take out the comments and it should be fine)

[php]
#!/usr/bin/env python
#flagHandler.py

#Script that determines if a flag is present and the order of the flag compared to other flags.
#Send in a list of all the flags your program supports, the second list should contain a list of
#the flags whose order matters relative to the other flags. The second list of flags must only
#have flags that are also contained within the allFlags list.
#This module returns a tuple with 4 values, the first one is a list of tuples with the flag letter
#and that flag's index for all flags that were found in argv[1], the second one returns a tuple of
#flags with their indices relative to other order-dependant flags, the third element returns any
#flags that weren't present in the allFlags list, and the fourth returns a boolean value depending
#on if a hypen(-) was found, to determine if flags were entered or not.



class G:
    flagDict = {} #flag dictionary holding flags and their corresponding index values
    flags = ''

def makeFlagDict(argv):
    G.flags = argv[1][1:]
    for i in range(len(G.flags)):
        G.flagDict[G.flags[i]] = i
        
def determineFlagsPresent(orderMatters):
    temp = 0
    delList = []
    for i in range(len(orderMatters)):
        try:
            temp = G.flagDict[orderMatters[i]]
        except:
            delList.append(orderMatters[i])
    for i in range(len(delList)): 
        orderMatters = delItemInList(delList[i],orderMatters)
    return orderMatters

def findRelativeOrder(listOfIndicies):
    relativeOrder = []
    for i in range(len(listOfIndicies)):
        relativeOrder.append((listOfIndicies[i][0],i))
    return relativeOrder   

def retrieveFromDict(key):
    try:
        return G.flagDict[key]
    except:
        return G.arbitraryIndexValue
    
def delItemInList(item,l):
    for i in range(len(l)):
        if l[i] == item:
            del l[i]
            return l
    return l
    
def findArgIndicies(orderMatters,argv):
    orderMatters = determineFlagsPresent(orderMatters)
    if len(orderMatters) < 2:
        for i in range(len(argv[1])):
            if orderMatters == []:
                return []
            elif argv[1][i] == orderMatters[0]:
                return [(orderMatters[0], G.flagDict[orderMatters[0]])]
        return []
    else:
        orderedList = []
        for i in range(len(orderMatters)):
            if i == 0:
                orderedList.append((orderMatters[i],retrieveFromDict(orderMatters[i])))
            else:
                for j in range(len(orderedList)):
                    if G.flagDict[orderMatters[i]] < orderedList[j][1]:
                        try:
                            while G.flagDict[orderMatters[i]] < orderedList[j-1][1]:                                
                                j-=1
                        except:
                            pass
                        orderedList.insert(j, (orderMatters[i],G.flagDict[orderMatters[i]]))
                        break
                    elif G.flagDict[orderMatters[i]] > orderedList[j][1]:
                        try:
                            while G.flagDict[orderMatters[i]] > orderedList[j+1][1]:                                
                                j+=1
                        except:
                            pass
                        orderedList.insert(j+1, (orderMatters[i],G.flagDict[orderMatters[i]]))
                        break
        return orderedList

def flagFound(item,allFlags):
    for i in range(len(allFlags)):
        if allFlags[i] == item:
            return True
    return False

def checkForIllegalFlags(allFlags):
    illegalFlags = []
    for i in range(len(G.flags)):
        if not flagFound(G.flags[i],allFlags):
            illegalFlags.append(G.flags[i])
    return illegalFlags
    
def checkForFlags(argv):
    if argv[1][0] == '-':
        return True
    else:
        return False    

def getFlagList(allFlags,orderedFlags,argv):
    illegalFlags =[]
    if checkForFlags(argv):
        makeFlagDict(argv)
        illegalFlags = checkForIllegalFlags(allFlags)
        argIndices = findArgIndicies(allFlags,argv)
        relOrder = findRelativeOrder(findArgIndicies(orderedFlags,argv))
        return (argIndices,relOrder,illegalFlags,True)
    else:
        return ([],[],[],False)
[/php]

---

### Post by eightmillion on 2009-10-12
> **ghostdog74 said:**
> so what's the difference between this and what filecmp module provides?

This filecmp module, as far as I'm aware, doesn't actually show the differences between files. It only reports if files/directory contents differ. It's comparable to the difference between "diff" and "diff -q".

---

### Post by ghostdog74 on 2009-10-12
> **eightmillion said:**
> This filecmp module, as far as I'm aware, doesn't actually show the differences between files. It only reports if files/directory contents differ. It's comparable to the difference between "diff" and "diff -q".
but you see, i have only given you part of it. see [filecmp]("http://docs.python.org/library/filecmp.html"). It will direct you to [difflib]("http://docs.python.org/library/difflib.html#module-difflib") for comparing files

---

### Post by eightmillion on 2009-10-13
> **ghostdog74 said:**
> but you see, i have only given you part of it. see [filecmp]("http://docs.python.org/library/filecmp.html"). It will direct you to [difflib]("http://docs.python.org/library/difflib.html#module-difflib") for comparing files

I am aware of difflib but not sure what it has to do with my stated goal of compacting Siph0n's code as much as possible, or why you're being so roundabout.

---

### Post by StunnerAlpha on 2009-10-13
> **eightmillion said:**
> I am aware of difflib but not sure what it has to do with my stated goal of compacting Siph0n's code as much as possible, or why you're being so roundabout.

He is just wondering what is so special about your script and why you would re-invent the wheel. Also I don't think he knows that you compacted someone else's code and thus is targeting you.

---

### Post by ghostdog74 on 2009-10-13
> **Siph0n said:**
> I wrote this one to find the differences in two files (two lists of employee ids) for work.

```
# Shawn McCarthy's Difference in two files
# 2007-11-21

readFile1=open('read1.txt', 'r')
readFile2=open('read2.txt', 'r')
writeFile=open('difference.txt', 'w')

readList1 = []
readList2 = []

# Create list from file 1
for line in readFile1:
    readList1.append(line.strip('\n'))

# Create list from file 2
for line in readFile2:
    readList2.append(line.strip('\n'))

readFile1.close()
readFile2.close()

writeFile.write('File 1 has these, but File 2 does not:\n')
for line in readList1:
    if line not in readList2:
        writeFile.write(line)
        writeFile.write('\n')

writeFile.write('\n')

writeFile.write('File 2 has these, but File 1 does not:\n')
for line in readList2:
    if line not in readList1:
        writeFile.write(line)
        writeFile.write('\n')

writeFile.close()
```

use set.

```

>>> a=set(open("file1").readlines())
>>> b=set(open("file2").readlines())
>>> print "things in file1 not in file2\n" + str(''.join(a-b))
things in file1 not in file2
8
1 2

>>> print "things in file2 not in file1\n" + str(''.join(b-a))
things in file2 not in file1
7
>>>


```

---

### Post by Siph0n on 2009-10-13
Thanks ghostdog74. I always like learning easier ways to do things :)

---

### Post by slakkie on 2009-10-13
Mostly shell function which I use for Debian/Ubuntu in order to maintain my boxes. Some are really handy when you are running alpha's or beta's or Debian unstable/testing.

Functions for Debian/Ubuntu:

```

## Debian apt functions

apt_update() {                                                     
    # If force option provided run update directly                 
    if [ -z "$1" ] ; then                                          

        local cache=$(stat -c "%Y" /var/cache/apt/pkgcache.bin)
        local sources=$(stat -c "%Y" /etc/apt/sources.list)    
                                                               
        # If sources.list is touched before cache created      
        # check if cache is too old                            
        if [ $cache -gt $sources ] ; then                      
            local now=$(date "+%s")                            
            cache=$((cache + 3600))                            
            [ $cache -gt $now ] && return 0                    
        fi                                                     
    fi                                                         
    sudo aptitude update                                       
    # If there is nothing to be updated, the .bin files        
    # are not updated, so this function will rerun the update.   
    # Prevent this from happing.                               
    sudo touch /var/cache/apt/pkgcache.bin                     
    # Clean the apt-file cache before updating remove repo's   
    # which are no longer in our sources file                  
    sudo apt-file purge                                        
    sudo apt-file update                                       
}                                                              

safe_upgrade() {
    apt_update  
    sudo aptitude -V safe-upgrade && purge_pkg
}                                             

## rmkernel
# NOT COMPATIBLE WITH DEBIAN
# Guaranteed to work under 9.10 
rmkernel() {
    local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
    local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
    local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"    
    sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
  purge_pkg
}                                                                                                               

purge_build_deps() {
    local i         
    for i in $* ; do
        sudo aptitude markauto \
        $(apt-cache showsrc $1 | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g')
    done                                                                                                      
    [ -n "$i" ] && purge_pkg                                                                                  
}                                                                                                             

purge_meta_pkg() {
    local i       
    for i in $* ; do
        sudo aptitude remove $i
        sudo aptitude markauto $(apt-cache depends $1 | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | awk '{print $NF}')
    done                                                                                                                      
    [ -n "$i" ] && purge_pkg                                                                                                  
}                                                                                                                             

purge_pkg() {
    sudo aptitude purge $(dpkg -l | tail -n +6 | grep -v '^ii' | awk '{print $2}')
    sudo aptitude clean                                                           
}                                                                                 

pkg2repo() {
    [ -z "$1" ] && return

    local pkg="$1"
    local policy  
    local cur     
    local can     
    local upgrade 

    for pkg in $@ ; do

    policy=$(apt-cache policy $pkg) 
    cur=$(echo -e "$policy" |  grep Installed | awk '{print $NF}')
    can=$(echo -e "$policy" |  grep Candidate | awk '{print $NF}')

    upgrade="$cur"

    [ "$can" == "(none)" ] && can=$cur 
    [ "$can" != "$cur" ] && upgrade="U: $cur > $can";

    repos=$(echo -e "$policy" | grep "$can" -A1 | egrep "(http|ftp|smb|cdrom|nfs|file)://" | tail -1 | awk '{print $2" "$3}')
    [ -n "$repos" ] && printf "%-56s %-35s %s\n" "$repos" "$pkg" "$upgrade" ;                                                
    done                                                                                                                     
}                                                                                                                            

repo2pkg() {
#    apt_update &>/dev/null
    local frepos=$@        
    local repos            
    for pkg in $(dpkg -l | grep '^ii'| awk '{print $2}' ) ; do
        repos=$(pkg2repo $pkg)                                
        if [ -z "$frepos" ] ; then                            
            [ -n "$repos" ] && echo -e "$repos"               
            continue                                          
        fi                                                    
        for i in $frepos ; do                                 
            echo -e "$repos" | grep -w "$i"                   
            [ $? -eq 0 ] && break                             
        done                                                  
    done                                                      
}                                                             

pkg_update() {
    repo2pkg | grep "U: "
}

rel2pin() {
    local prefs=/etc/apt/preferences.d/pkg2pin
    [ -e "$prefs" ] && sudo mv $prefs $prefs.rel2pin.$(date "+%Y%m%d")
    [ -n "$1" ] && echo "# $@" | sudo tee -a $prefs
    pkg2pin $(dpkg -l | grep "^ii" |awk '{print $2}')
}

pkg2pin() {
    [ -z "$1" ] && return

    local pkg
    local msg
    local prefs=/etc/apt/preferences.d/pkg2pin
    msg="$(date +'%Y%m%d:%H%M%S')"

    for pkg in $@ ; do
        pkg=$(dpkg -l "$pkg" 2>/dev/null)
        [ $? -ne 0 ] && continue
        pkg=$(echo -e "$pkg" | grep "^ii" |awk '{print $2" "$3}')
        echo -e "$pkg" | awk '{print "# Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
        #echo -e "$pkg" | awk '{print "Explanation: Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
    done | sudo tee -a $prefs
}

dpkg2pin() {
    [ -z "$1" ] && return

    local pkg
    pkg=$(dpkg -l | grep "^ii" |awk '{print $2}' | grep "$1")
    [ $? -ne 0 ] && return
    for i in $pkg ; do
        pkg2pin $i
    done
}

```


Misc functions
```

extract() {
        for i in $@ ; do
    [ ! -f "$i" ] || [ ! -r "$i" ] && echo "'$i' is not present or could not be read" && continue
    case $i in
      *.tar.bz2|*.tbz2) bzip2 -dc $i | tar xvf -    ;;
      *.tar.gz|*.tgz)   gzip -dc $i  | tar xvf -    ;;
      *.bz2)     bzip2 -dc $i     ;;
      *.rar)     rar x $i   ;;
      *.gz)      gzip -d $i   ;;
      *.tar)     tar xvf $i    ;;
      *.zip)     unzip $i   ;;
      *.Z)       uncompress $i  ;;
      *.7z)      7z x $i  ;;
      *.deb)     ar xv $i ;;
      *)         echo "'$i' cannot be extracted via extract()" ;;
    esac
        done
}
date2stamp() {
    date --utc --date "$1" +%s
}

stamp2date() {
    date --utc --date "1970-01-01 $1 sec" "+%Y-%m-%d %T"
}

```

This is a function I use to determine wheter I can source particial files in my .bashrc/.zshrc. It echo's the shell which I'm running since $SHELL is always set the the shell in /etc/passwd.

```

run_shell() {
    echo `ps -p $$ | egrep -v "PID|TTY|TIME|CMD" | awk '{print $NF}' | sed -e 's/[^A-Za-z0-9]//g'`
}                                                                                                 

```

Print .doc files or .xls files via the command line:

```

SELF=`basename $0`

# What we are determines what we do :)
if [ "$SELF" = "print_doc" ] ; then
  FUNC=print_word
elif [ "$SELF" = "print_excel" ] ; then
  FUNC=print_excel
fi

print_word() {
  antiword -f -a a4 "$1" | a2ps -
}

print_excel() {
  xlhtml "$1" | a2ps -1 -
}

# Fix for LANG settings which are not supported..
LANG_OLD=$LANG
unset LANG
for i in "$@" ; do
  $FUNC "$i"
done
# And back to the old values
export LANG=$LANG_OLD

```

---

