---
title: "Perl CSV parsing help"
date: 2008-06-08
forum: Programming Talk
---

### Post by ElementC on 2008-06-08
I administrate an ubuntu-based Half-life 2 Deathmath server. I've been working on a stats system for a while and have most of the layout and structure knocked out, but I have one last, apparently very complicated, chunk to do and I'm completely out of my depth here. See, I need a way to process a CSV ranks file and export the data as follows:

Line 0 is a header, listing the title of each column
Lines 1-10 is the top ten players , with the following columns listed: rank(column 03), name(column 12), kills (column 07), deaths (column 05), headshots (column 06), and finally total time online(column 10). They can be comma separated or tab separated so long as its consistent and, thankfully, the lines are sorted by rank already.
Line 11 should be the total number of headshots, so add up column 6.
And line 12 should be the total number of kills, so add up column 7.

All of this should just printf (or whatever perl calls it) out to stdout.

I've basically gotten the bash script to take all this data together and smash it into a report for nightly email and such knocked out and I'm rather proud of it, but I've not done a bash script in a while, so I'll post it up here for you all to look over and point out any blinding errors.
```
#!/bin/bash
# stats.sh
# Script to process stats from Hl2MP Mani-Admin Mod's rank database files for use in a nightly email.
# Written by  Casey '(ttm)ElementC' Doran  6-8-2008.
# Revision 12.
#
# Set some file locations and other variables.
# The Variables MAILSUBJECT and MAILADDRESS have no use right now; uncomment the mail section to enable auto-email of the file with these variables.
STATFILE=~/srcds/hl2mp/cfg/mani_admin_plugin/data/mani_stats.txt
RANKFILE=~/srcds/hl2mp/cfg/mani_admin_plugin/data/mani_ranks.txt
OUT=~/stats.txt
PERLOUT=~/perlout.txt
TEMPTOPTEN=~/tmptptn.txt
SERVERNAME='(ttm)LogravKillbox'
SERVERADDRESS='catsceo.servebbs.net:27015'
RUNTIME=`date`
GAMENAME='Half-Life 2 Deathmatch'
MOTD=~/srcds/hl2mp/motd.txt
MAILSUBJECT=Nightly rank email.
MAILADDRESS=Listof email addresses here.
# Get ourselves ready to run and clean up from last time we ran
cd ~
rm $OUT
rm $TEMPTOPTEN
rm $PERLOUT
# Obtain some general data.
RANKEDUSERS=`cat $RANKFILE| wc -l`
TOTALUSERS=`cat $STATFILE | grep na| wc -l`
#  Here is where we would run the perl script to list the top ten players and list the total number of kills and headshots. It's not finished yet, but I'll write in the code  just for completion purposes.
./parser.pl>$PERLOUT
# We set the variable for total number of kills (found by totaling column  7 of $RANKFILE) here. It should be the last line of the perl output.
KILLTOTAL=`cat $PERLOUT|tail -1`
# We set the variable for total number of headshots (found by totaling column  6 of $RANKFILE) here. It should be the second to last line of the perl output.
HEADSHOTTOTAL=`cat $PERLOUT|tail -2|head -1`
# Here, we remove the extra 2 lines from the end of the perl script's output. We've already set them as variables so it /should/ be safe.
cat $PERLOUT | head -11>$TEMPTOPTEN
# Now that we have all of our data stored (theoretically, at least) we can start  echo -eing out the final report. It could all be done in two echo -e statements, but for readability I'm just gonna break them up by coherent sentence, with multiple linebreaks on a single line for space savings (I'm not *that* wierd)
echo -e "$SERVERNAME Info for $RUNTIME" >$OUT
echo -e "Server can be connected to by pasting steam://connect/$SERVERADDRESS in your browser with steam and $GAMENAME installed.">>$OUT
echo -e "Server has $TOTALUSERS, of which $RANKEDUSERS are ranked.">>$OUT
echo -e "Our ranked players have made a total of $KILLTOTAL kills, of which $HEADSHOTTOTAL were headshots.">>$OUT
echo -e "The top ten ranked players (as determined by total number of kills) are as follows:">>$OUT
cat $TEMPTOPTEN>>$OUT
echo -e "MESSAGE FROM THE ADMIN:">>$OUT
cat $MOTD>>$OUT
#Automailer. Uncomment to enable it.
#/usr/bin/mail -s $MAILSUBJECT $MAILADDRESS < $OUT

```

Anyone willing to help with the perl script to process the CSV file? I've gotten libtext-csv-perl installed, supposedly its a perl module that simplifies the whole process, but I don't have a clue how to work perl. I'll include a copy of the mani_ranks.txt (I had to edit out the IP and steam addresses for privacy purposes on a Windows box, you might need to run it through dos2unix before its usable) and the readme from the ranks plugin that explains the fields for you all.

Thanks in advance, folks.

-E/C

---

### Post by askreet on 2008-06-08
Unfortunately I don't have the time to write the whole script, but have you considered using Ruby.  You can do something like this pretty effortlessly in Ruby.

file = File.new("readfile.rb", "r")

while (line = file.gets)
  # create an array of columns seperated by ,'s.
  a_values = line.split(",")

  # do stuff with them, like print:
  printf "#{a_values[0]}\t#{a_values[1]}\n"
end
file.close

---

### Post by ElementC on 2008-06-08
Thanks askreet, I hadn't thought to use something non-perl. now that I think about it, does anyone know if python is capable of this? I'd really rather not install a whole new interpreter, it's not my physical or root-access box, so It's best not to bother the admin at this hour if I can do it in python.

-E/C

---

### Post by unutbu on 2008-06-08
```
#!/usr/bin/perl
use strict;
use warnings;
use Text::CSV;

my $csv = Text::CSV->new({binary => 1});
my @rank;
open(CSV,"<","$ENV{RANKFILE}") || die;
my $num_headshots=0;
my $num_kills=0;
while (my $line=<CSV>) {
    my $status = $csv->parse($line);
    if ($status) {
	my @columns=$csv->fields();
	my $rank=$columns[3];
	my $kills=$columns[7];
	my $headshots=$columns[6];
	if ($rank<=10) {
	    my $name=$columns[12];
	    my $deaths=$columns[5];
	    my $tto=$columns[10];
	    push(@rank,[$rank,$name,$kills,$deaths,$headshots,$tto]) ;
	}
	$num_headshots+=$headshots;
	$num_kills+=$kills;
    } else {
	my $diag = $csv->error_diag();
	die "$diag";
    }
}
close(CSV);


my @dat=('Rank','Name','Kills','Deaths','Headshots','Time online');
format =
@<<< @<<<<<<<<<<<<<<<<<<<<<<<<<<<<<< @>>>>>   @>>>>>   @>>>>>>>>   @<<<<<<<<<<
@dat
.
write;

foreach (sort {$a->[0] <=> $b->[0]} @rank) {
    @dat=@{$_};
    write;
}

print "$num_headshots\n";
print "$num_kills\n";

```

Output:
```

Rank Name                             Kills   Deaths   Headshots   Time online
1    (ttm)Celena                       1863     1230           0   69507
2    (ttm)Sìth                        1031      903           0   43617
3    (ttm)howling_wind                  583      402           0   24990
4    (ttm)ElementC                      282      483           0   31609
5    (MAC)MASTER AND COMMANDER          119      138           0   6493
6    SMUT MUFFIN =MM=                    69       73           0   1674
7    RoX l @Wulff@                       62      107           0   4378
8    TeCarlo7                            57       76           0   4458
9    bob                                 55       31           0   2331
10   Th1rst3y b4$t4RD                    52       96           0   3256
0
4629

```

---

### Post by ElementC on 2008-06-08
As I expected of the ubuntu community, fast, accurate, and concise answers.
You, good sir, deserve a medal.

Do you mind if I distribute it with a GPL package (do you release this under GPL)?

This looks like it will be it, thank you all for all your help!

-E/C

---

### Post by ghostdog74 on 2008-06-08
```

awk 'BEGIN{
 FS=","
 printf "%-15s%-25s%15s%15s%15s%15s\n","Rank","Name","Kills","Death","headshots","TotalTime" 
}
NR<=10{
gsub(/[[:space:]]$/,"",$NF)
printf "%-15s%-25s%15s%15s%15s%15s\n",$4,$NF,$8,$6,$7,$11
}
{
  headshots+=$7       
  kills+=$8
}
END{
 print "headshots: ", headshots    
 print "Kills: ", kills    
}' mani_ranks_example.txt

```

output:
```

# ./testnew.sh
Rank           Name                               Kills          Death      headshots      TotalTime
1              (ttm)Celena                         1863           1230              0          69507
2              (ttm)Sìth                          1031            903              0          43617
3              (ttm)howling_wind                    583            402              0          24990
4              (ttm)ElementC                        282            483              0          31609
5              (MAC)MASTER AND COMMANDER            119            138              0           6493
6              SMUT MUFFIN =MM=                      69             73              0           1674
7              RoX l @Wulff@                         62            107              0           4378
8              TeCarlo7                              57             76              0           4458
9              bob                                   55             31              0           2331
10             Th1rst3y b4$t4RD                      52             96              0           3256
headshots:  0
Kills:  4629


```

---

### Post by ElementC on 2008-06-08
I'll keep that bookmarked, but unutbu's was working first for me, it ain't broke so not fixing it.

meantime, heres the final output of the project:
> (ttm)LogravKillbox Info for Sun Jun  8 23:33:44 EDT 2008
Server can be connected to by pasting steam://connect/catsceo.servebbs.net:27015 in your browser with steam and Half-Life 2 Deathmatch installed.
Server has 51, of which 37 are ranked.
Our ranked players have made a total of 4695 kills, of which 0 were headshots.
The top ten ranked players (as determined by total number of kills) are as follows:
rank,name,kills,deaths,headshots,total time online
1,(ttm)Celena,1905,1254,0,71092
2,(ttm)SÃ¬th,1055,945,0,45187
3,(ttm)howling_wind,583,402,0,24990
4,(ttm)ElementC,282,483,0,31609
5,(MAC)MASTER AND COMMANDER,119,138,0,6493
6,SMUT MUFFIN =MM=,69,73,0,1674
7,RoX l @Wulff@,62,107,0,4378
8,TeCarlo7,57,76,0,4458
9,bob,55,31,0,2331
10,Th1rst3y b4$t4RD,52,96,0,3256
MESSAGE FROM THE ADMIN:
Keep these rules in mind in order to get the most enjoyment out of your time here:
1.Keep the language clean.
2.No camping.
3.No spamming.
4.Listen to any (ttm) members on this server.
5.Report any hackers or cheaters or laggers to me, (ttm)ElementC via SteamIM or email immediatley.
6.Have Fun!

LATEST NEWS:
- Fixed the stats system for real this time. If you want to be on the email list that gets the scoreboard once weekly, email me at [email]wer4geeks@gmail.com[/email] and I'll add you to the list.
- Implemented a high-ping kicker. So don't have a high-ping.
- Testing the auto-notification for when we go gravguns only. Probably fails a lot, so disregard it if you're getting wierd gravgun only messages unless theres a group of (ttm)'ers yelling at you.
- Working on fixing headshots. Thats some screwed up configs right thurr.

There are a lot of you that were regulars on this server before we went down. You should be happpy to know that in the time we were out, our ISP doubled our bandwith, we added another gig of ram or so, we went from Debian Etch to Ubuntu hardy in the OS department, installed a 10,000 RPM Raptor HD, and are now using a native x64 build of our OS.
Of special note is, as always, our gracious Host, CatsCEO of the UbuntuFlorida Local Community team. He's been with ClanTTM in spirit since the beginning and anyone who plays here really owes him a hug.
Heres to a lot of fun ahead!

Fondest Regards,

(ttm)ElementC
Server Admin
Sunday, June 8, 2008
23:34:31 EDT


Looks quite nice, but apparently my headshot detector is broken. Ah well, that's not within the scope of this forum. Thank you all so very much; I'm bookmarking this thread if only to see the creative ways you all come up with that.

And if anyone can tell me how to configure "nail" to automail that so I don't have to install a mailserver, I'd be pretty much in love with you all.

@ghostdog74: Awk? really? Never thought it was suited for arrays. Then again, basic sed-like stuff is all I ever used it for XD.

---

### Post by ghostdog74 on 2008-06-08
> **ElementC said:**
> 
@ghostdog74: Awk? really? Never thought it was suited for arrays.

what do you mean by "really"? . Anyway, awk is the grandfather of Perl, and of course its suited for arrays. Its called associative arrays

> 
 Then again, basic sed-like stuff is all I ever used it for XD/
awk is more powerful and flexible than sed, especially when you deal with structured data

---

### Post by ElementC on 2008-06-09
Never really thought of using awk, maybe because I never really learned it beyond the first few chapters of bash cookbook in barnes and noble one day. Next time, that will be my first plan of action. Thanks, mate.

---

### Post by slavik on 2008-06-09
awk was the original flat file database. :)

---

### Post by ElementC on 2008-06-09
You learn something new every day. Your signature is very relevant too, slavik. 

1: I could google it, but you all would know better: what are some good awk references out there?

2: Anyone have any tips on mailing this thing out? I have the line you see at the end of the .sh, but it only works for internal users (ie elementc@localhost). Someone told me to use "nail" but I'm not sure what it is, what configs need to be tweaked, how to integrate it with my script, etc.

3: And how would I add it as a cron job? It needs to be run as user srcds once daily.

I know that this is probably teetering on the edge of off topic, but to me automation is programming, no matter how simple it is. And besides, why start a new thread somewhere else when we're on a roll here?

Thanks, folks.

-E/C

---

### Post by ghostdog74 on 2008-06-09
> **ElementC said:**
>  what are some good awk references out there?

see [here]("http://www.unix.com.ua/orelly/unix/sedawk/index.htm")

---

### Post by pmasiar on 2008-06-09
> **ElementC said:**
> I hadn't thought to use something non-perl. now that I think about it, does anyone know if python is capable of this?

Yes, python is capable of anything what Perl or Ruby does, and code will be more readable than Perl, and faster than Ruby :-) And no Python expert looked at your post because of your title, so...

Simplest way will be just plain CGI, using Python's cgi module. To get you idea how to start: [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)

If you want to be more fancy, take a look at Django web app framework.

---

### Post by unutbu on 2008-06-09
Feel free to distribute the perl script with a GPL package.

If you have any players whose name includes a comma, such as U,nutbu
then make sure the name is put in quotes in the rank file:
```

SteamID Here,IP HERE,1212975641,1,1589,1230,0,1863,105,0,69507,0,"U,nutbu"

```

> 1: I could google it, but you all would know better: what are some good awk
references out there?

@ElementC, here is a tutorial on Awk that I like: [http://www.grymoire.com/Unix/Awk.html](http://www.grymoire.com/Unix/Awk.html).


@ghostdog74, I get 

> Sorry, but access to this page is closed now.
If you search study materials or ebooks for cisco certification - request it in our Cisco Career Certifications forum

when I go to [http://www.unix.com.ua/orelly/unix/sedawk/index.htm](http://www.unix.com.ua/orelly/unix/sedawk/index.htm). Is the link broken or do I need to purchase a license?

> 2: Anyone have any tips on mailing this thing out? I have the line you see at
the end of the .sh, but it only works for internal users (ie
elementc@localhost). Someone told me to use "nail" but I'm not sure what it is,
what configs need to be tweaked, how to integrate it with my script, etc.

Create a user account on the server. Create a file called .forward in the new user's home account.
Each line of the .forward file should contain one email address. 
When you send mail to the new user, the message will get forwarded to all addresses in the .forward file.
MAILADDRESS can be just the one new user @localhost.

> 3: And how would I add it as a cron job? It needs to be run as user srcds once
daily.

Log in as srcds. Type

```
crontab -e
```

Add this line:
```
30 18 * * *  /path/to/stats.sh
```

The script will run at 6:30pm every day.

---

### Post by ghostdog74 on 2008-06-09
> **unutbu said:**
> 
@ghostdog74, I get 

when I go to [http://www.unix.com.ua/orelly/unix/sedawk/index.htm](http://www.unix.com.ua/orelly/unix/sedawk/index.htm). Is the link broken or do I need to purchase a license?



some areas restrict access to this site. For me, its working link. Another great resource is the official GAWK manual.

---

### Post by unutbu on 2008-06-09
I edited my original perl script (post #4) to have prettier output -- like ghostdog74's. It will also sort the lines by rank so it is not strictly necessary to keep the rank file in order.

---

### Post by ElementC on 2008-06-09
The updated script is great, but is there a way to have it read the location of the ranks file from the system variable I set in the bash script? I'm thinking of packaging this for other users of this rank system, (crediting you guys of course) and and it'd be nice to only have to set it once.

---

### Post by unutbu on 2008-06-09
I could make the perl script parse the shell script, but that ain't kosher.

A better way of handling this would be to put 

```
RANKFILE=~/srcds/hl2mp/cfg/mani_admin_plugin/data/mani_ranks.txt
export RANKFILE

```
in ~/.profile

Then your bash script will know about $RANKFILE automatically, and the perl script can access the environment variable through $ENV{RANKFILE}. (I edited my post #4 to do this).

---

