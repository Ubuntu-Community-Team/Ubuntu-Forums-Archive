---
title: "Fake &quot;Hax0r / Hacker Activity&quot; bash script"
date: 2007-06-10
forum: Programming Talk
---

### Post by Tundro Walker on 2007-06-10
EDIT (6/13/07): uploaded an even newer .zip, this one containing...
[LIST]
[*]more statement constructs, including the use of prepositional phrases, multiple adjectives, etc (all while still making sense when read!)[/LIST][LIST]
[*]"end-phrases" are now called "exclamations" and can get tacked on the beginning and end of statements.  exclamations use their own "word list" file, so you can add your own to it, including more emoticons, which I started adding to it (lol)[/LIST][LIST]
[*]neutered the sub-console...it can't spawn more sub-consoles anymore[/LIST][LIST]
[*]more words in the word lists[/LIST][LIST]
[*]phrases get dumped to a log file while scripts are going, letting you go back and see a play-by-play of the action (just like a real hax0r...LOL...)[/LIST][LIST]
[*]better code...farmed off some repetitious code to sub-scripts that are called by the various main scripts.  (still trying to figure out how to get the array loading code to operate like this some how...can't figure out a way to get a sub-script to build an array and make it global for all terminals to see, or to at least pass the darn thing back to the calling script so it can use the loaded array...ugh)[/LIST](new screenshot)

Stupidest phrases I've seen so far...

> 
"Replacing The Man's Enhancement plus Piggy-backed Datasofts..."
"Goin Pirate all over Surveillance Sci-Ops Download"
"Pwn Security Variables on PYTHON Code"
"Reseed Tundro's Bin despite Anonymous Counter-Intelligence!"
"Prevent id10t Command!"
"Snipe Unknown WOW Identity"
"Bugging Bio-Tech Macro like Microsoft Virus"
"SCREWED!...Compare Shaft-able Hax0r plus Bugged Libraries!"
"Increased Difficulty!...Llama's in ur Exception, Neutralize ur Protocols!!"
"im in ur Router, Streaming ur Replication!"

...and my all time favourite to date...

"Parsing Illegal Pr0n via MPAA Rules"
~~~~~~~~~~~~~

If you want the back-story on this, [see here...]("http://ubuntuforums.org/showthread.php?t=452850")

Basically these are some scripts that spam fake "haxor-like" activity to your screen...console messages, progress-meter gui's, sub-consoles, etc.  It's not actually doing anything except generating random action phrases, spamming them to things (consoles, gui, etc), and sleeping in between.

This was my first foray into bash scripting, and I probably wouldn't have done it if it wasn't so ridiculously stupid (hehe).  Anyways, check out the screenshot, d/l the .zip file (~140kb), and read the "readme" to learn how to use it.  (Pretty simple, just give the scripts executable rights, open a console, and fire off the "main" script, using a command-line argument to let it know how many fake actions it should take.)

Have Fun!

---

### Post by steveneddy on 2007-06-10
This is stupid.

---

### Post by ankursethi on 2007-06-11
> **steveneddy said:**
> This is stupid.

Yes. And fun. Really, I can leave this on instead of a screensaver. I can already imagine the look on the faces on my Windows using buddies :popcorn:

---

### Post by steveneddy on 2007-06-11
Ooo - look - I'm a fake haxor - OOooo - his screen does twiddly stuff....whatever

---

### Post by ankursethi on 2007-06-11
> **steveneddy said:**
> Ooo - look - I'm a fake haxor - OOooo - his screen does twiddly stuff....whatever

Well, most of the Windows guys think I'm a sup4|-| 1337 h4x0r when I clean up their systems with CCleaner and Ad Aware to make it "go faster". They'll go crazy if they see "Processing God-Level Servers" on my screen.

It's a cute little thing. Enjoy it.

---

### Post by steveneddy on 2007-06-11
> **ankursethi said:**
> Well, most of the Windows guys think I'm a sup4|-| 1337 h4x0r when I clean up their systems with CCleaner and Ad Aware to make it "go faster". They'll go crazy if they see "Processing God-Level Servers" on my screen.

It's a cute little thing. Enjoy it.

whatever

---

### Post by Motoxrdude on 2007-06-11
Hahah, that's awesome. Thanks man, thats pretty tite.

---

### Post by sweetooth on 2007-06-11
-yup

---

### Post by kvonb on 2007-06-11
> **steveneddy said:**
> Ooo - look - I'm a fake haxor - OOooo - his screen does twiddly stuff....whatever


Why do you have to be so rude and obnoxious?

The guy supplies the scripts that he wrote which could be extremely useful to anyone who is trying to learn scripting using X dialogue pop-ups, which I would class as quite useful.

If  you can do better, why not contribute something of much more use than arrogance?

---

### Post by Chayak on 2007-06-11
That reminds me a bit of the screensaver I use at work for my windows machine, a BSOD, now that tends to freak people out the first time they see it.

---

### Post by ageilers on 2007-06-11
I love your Hello Kitty Icon. Is that available as a background?

---

### Post by Tundro Walker on 2007-06-11
> **ageilers said:**
> I love your Hello Kitty Icon. Is that available as a background?

I've attached the "HelloKittyXP" logo I made, and the Ubuntu-Kitty wallpapers ChipX86 made.

I use the XP one at work for my screensaver (on, you guess it, my WinXP comp).  I choose "picture gallery" screensaver, set the  background to black, pic positioning to random, then have it load pics from a folder that only has that HelloKittyXP logo in it.  The end-result is it bounces around on a black screen just like the default windows logo.

~~~~~~~~~~~~~~~~~

As for Steveneddy, everyone's entitled to an opinion, and I actually agree with his point.  It's annoying watching some folks show-boat like they're "the man" when they're not.  (like folks at the club getting their picture taken behind the DJ booth like their tearing up some tracks, when actually they don't know their way around a turn-table.  Or, those tuner folks that add spoilers to their cars, and think that makes them a know-it-all about cars, but they don't know how to really overhaul an engine and optimize it for performance.)

But, I thought this was such a funny project that kinda made fun of the whole "leet haxor gangsta" thing, so I was compelled to do it.  And, I learned some bash scripting while I was at it.  I team it with BrightSide, which gets it to execute when I toss my mouse into the lower-right corner.   Not as good as a real screensaver ('cause your computer's still going, and anyone can just walk up and do stuff on it).  But with all the activity on it, I think most folks would be a little paranoid about touching a computer that's "Cracking FBI Firewalls".  LOL!

NOTE: I've edited the original post to put a better .zip file in.  The first one was overly complex to randomize the action, and didn't seem to fire off sub-consoles very often.  So, I made it simpler and it fires them off a little more.

---

### Post by Mathiasdm on 2007-06-11
> **Tundro Walker said:**
> 
But, I thought this was such a funny project that kinda made fun of the whole "leet haxor gangsta" thing, so I was compelled to do it.
Yep, same here, it just looked like a funny thing to try. Here's my program from the other thread (it doesn't use the sleep function, for 2 reasons. The first is that it makes your fans make a lot of noise, so it actually seems like you're computer is working :p Secondly, I wrote this program while on Windows, where the implementation of sleep is apparently different.). Anyways, it's fun, join us!

```

#include <time.h>
#include <stddef.h>
#include <iostream>
#include <string>

using namespace std;

int main(void) {
	cout << "World domination -- Program Loading" << endl;
	for(long i=0;i<110000000;i++) {
		if(i%10000000 == 0) {
			cout << (i/1000000) << " % complete..." << endl;
			for(long j=0;j<10000*((long)rand());j++) {
				j++;
				for(long k=0;k<10000;k++) if(k==99) j--;
				//Niks!
			}
		}
	}
	for(long i=0;i<(1+rand()%3)*100000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << "3 possible intruders detected:" << endl;
	cout << "     Scanning intruder properties";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << ".";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << ".";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << ".";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << endl << "WARNING: weapons detected." << endl << "Eliminate intruders? (Y/N) ";
	string s;
	cin >> s;
	char c = s.at(0);
	if(c=='n' || c=='N') {
		cout << endl << "Terminating program -- Please try our World Domination Express pack: only €99 for a world of fun!" << endl;
		return 0;
	}
	else if(c!='y' && c!='Y') {
		cout << endl << "Error: incorrect answer.\n       Extermination started." << endl;
		cout << c << endl;
		return 0;
	}
	cout << "Intruders eliminated..." << endl;
	cout << "Preparing particle beam accelerator NK3000" << endl;
	for(long i=0;i<(1+rand()%3)*20000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << "Targets selected:" << endl;
	cout << "    *New York" << endl;
	cout << "    *Washington" << endl;
	cout << "    *London" << endl;
	cout << "    *Paris" << endl;
	cout << "    *Moscow" << endl;
	cout << "    *Mumbai" << endl;
	cout << "    *Berlin" << endl;
	cout << "    *Venice" << endl << endl;
	cout << "Pressing the red button..." << endl;
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << "Error: buffer overflow. Extra target: " << endl;
	cout << "     *you" << endl;
	cout << "You will be assimilated. Resitance is futile." << endl;
	cout << "ERROR: lost carrier." << endl;
	return 0;
}

```

---

### Post by Sockerdrickan on 2007-06-11
I lol'd

---

### Post by Tundro Walker on 2007-06-11
Heh, others hack their computer for fun and profit.  We're just hoaxing it for fun.

---

### Post by Motoxrdude on 2007-06-11
Going ninja on FBI tables.

LMAO.

---

### Post by Ramses de Norre on 2007-06-11
> **Mathiasdm said:**
> Yep, same here, it just looked like a funny thing to try. Here's my program from the other thread (it doesn't use the sleep function, for 2 reasons. The first is that it makes your fans make a lot of noise, so it actually seems like you're computer is working :p Secondly, I wrote this program while on Windows, where the implementation of sleep is apparently different.). Anyways, it's fun, join us!

```

#include <time.h>
#include <stddef.h>
#include <iostream>
#include <string>

using namespace std;

int main(void) {
	cout << "World domination -- Program Loading" << endl;
	for(long i=0;i<110000000;i++) {
		if(i%10000000 == 0) {
			cout << (i/1000000) << " % complete..." << endl;
			for(long j=0;j<10000*((long)rand());j++) {
				j++;
				for(long k=0;k<10000;k++) if(k==99) j--;
				//Niks!
			}
		}
	}
	for(long i=0;i<(1+rand()%3)*100000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << "3 possible intruders detected:" << endl;
	cout << "     Scanning intruder properties";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << ".";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << ".";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << ".";
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << endl << "WARNING: weapons detected." << endl << "Eliminate intruders? (Y/N) ";
	string s;
	cin >> s;
	char c = s.at(0);
	if(c=='n' || c=='N') {
		cout << endl << "Terminating program -- Please try our World Domination Express pack: only &#8364;99 for a world of fun!" << endl;
		return 0;
	}
	else if(c!='y' && c!='Y') {
		cout << endl << "Error: incorrect answer.\n       Extermination started." << endl;
		cout << c << endl;
		return 0;
	}
	cout << "Intruders eliminated..." << endl;
	cout << "Preparing particle beam accelerator NK3000" << endl;
	for(long i=0;i<(1+rand()%3)*20000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << "Targets selected:" << endl;
	cout << "    *New York" << endl;
	cout << "    *Washington" << endl;
	cout << "    *London" << endl;
	cout << "    *Paris" << endl;
	cout << "    *Moscow" << endl;
	cout << "    *Mumbai" << endl;
	cout << "    *Berlin" << endl;
	cout << "    *Venice" << endl << endl;
	cout << "Pressing the red button..." << endl;
	for(long i=0;i<(1+rand()%3)*30000000;i++) {
		i++;
		do {
			i--;
		}
		while(false);
	}
	cout << "Error: buffer overflow. Extra target: " << endl;
	cout << "     *you" << endl;
	cout << "You will be assimilated. Resitance is futile." << endl;
	cout << "ERROR: lost carrier." << endl;
	return 0;
}

```

What is the purpose of these:
```
		do {
			i--;
		}
		while(false);
```
They seem like a tremendous stupid way to say **i--;** ...

---

### Post by Mathiasdm on 2007-06-11
> **Ramses de Norre said:**
> What is the purpose of these:
```
		do {
			i--;
		}
		while(false);
```
They seem like a tremendous stupid way to say **i--;** ...
Good point ;)
Basically, I figured the compiler might change
```

i++;
i--;

```
into nothing, seeing as it really doesn't do anything.

The whole point of that extra code is to just make the computer seem busy (making the fans make noise and such ;) ). So yes, it's silly code, but it's intentional :p Don't look at it for programming tips ;) (For example: I should've made a 'sleep' function, instead of just copy/paste-ing that part over and over again.)

---

### Post by NeoGreen on 2007-06-11
Man, that is cool.  :D

---

### Post by Tundro Walker on 2007-06-12
I've been tweaking the script, mostly trying to optimize the code ... got a lot of redundant code that I can't figure out how to farm into functions or separate scripts that I can call, and I can't figure out how to just load the list arrays once and not have to do it every time the script is recalled.  That's turning into a problem, because as the lists get larger, I'm noticing a pause before a sub-console opens up...it's taking like a second to compile the word list arrays in its own console session.  If I could figure out a way to load the word lists arrays as some kind of global "env" array variables that all console windows could see, then the main script would just do the loading, and all sub-consoles, progress-meters, etc would just use the words in those lists instead of redundantly trying to build their own each time they show up.  Blech.

Anyways, I was also messing with different statement structures.  The posted scripts just use VERB + ADJ + NOUN.  I wanted to mix that up by adding more adj's and/or prepositional phrases (you know, the things in the sentence that usually tell you where something went or with whom...in the house, on  the bed, with the girl, etc).  I got it going, but it's pretty hit or miss on the statements.  Check out the screenshots to see what I mean.  Some of those are pretty good, but others...not so much.

I basically copied a preposition list from the net, and I think I need to weed it out some (EG: "unto"...no hax0r "unto's" anything.  "Hacking unto Database!"  NOT!)

Anyways, when I clean up the scripts a bit more, I'll post a new copy in my original post on this thread.

---

### Post by bl3s5in on 2007-06-12
./script_main.sh: line 105: ((: i <  : syntax error: operand expected (error token is " ")

lulwut

---

### Post by ankursethi on 2007-06-12
You need to pass the number of actions to be executed to the script as a commandline parameter.

---

### Post by Tundro Walker on 2007-06-12
Speaking of show-boating as something we're not, some MIT folks have designed a [fake technical paper generator]("http://pdos.csail.mit.edu/scigen/").  

I was itching to try this out, and someone at work asked a question about why an internal site couldn't do something or some such.  The real answer to his question was "no we can't do that", but I decided to tack on one of these puppies just to add clout to my answer (but mostly to see what kind of reaction it got.)  He replied to my answer by saying "oh, well, I don't quite understand all that, but I guess that answers my question."  LOL!

I printed off a copy of what I sent that guy, and brought it home for my IT roommate to read, talking it up like it was some new, stellar concept in computing that was going to change the way we do things in the next 5 years.  He was excited to read it, but about half-way through he gave up, saying "this is either complete bull-crap, or beyond my IQ level."  :D

Ah, good times.

---

### Post by kvonb on 2007-06-13
> **Tundro Walker said:**
> Speaking of show-boating as something we're not, some MIT folks have designed a [fake technical paper generator]("http://pdos.csail.mit.edu/scigen/").  



Now we know where the politicians get all their speeches!

It's amazing how many people will accept what you are saying if you use lots of big words and confusing sentences!

---

### Post by Virgilius on 2007-07-10
Ha! Too true! But hey, the people around are quite gullible in real life! :D

---

### Post by fourthdimension on 2007-12-03
I love it!  Pretty funny.

---

### Post by sloggerkhan on 2008-02-12
hmm... this is mildly amusing.

---

### Post by marufaberlin on 2008-02-12
You do realize that the script has to be executable on the machine it's supposed to be run? I mean, if you want it to run on your own box as a screensaver or somewhat, that's no problem. But if you want to put it on a different machine to freak the other box's user out, without him noticing, maybe even without physical access, that's gonna be hard, if he isn't some kind of n00b.

---

### Post by KIAaze on 2008-05-20
Hi Tundro Walker,
I started implementing the stuff from ideas.txt. :)

Added files:
* whiptail_progressbar.sh: script to demonstrate the use of whiptail
* Operation_Overkill.py: [modification of the script created by blithen]("http://ubuntuforums.org/showthread.php?p=4974544#post4974544")
* boldtext.sh: bold text demo
* colors.sh: color demo
* oo.cfg: Operation Overkill configuration file! Here you can configure how many loops and with what probability each action runs.

Note: If you want all actions back again, uncomment the commented commands in eval_txt and change oo.cfg so that CASE_MIN=0 and CASE_MAX=100.
I hope the rest is self-explanatory.
If you have any questions, just ask.

Modified files:
* script_main.sh: implemented usage instructions (run without arguments to see them) + use of oo.cfg
* script_random_generator.sh: Fixed it so that it also works for numbers between 0 and 1 for example
* txt_evals: Added the new scripts I created in there + ./script_main itself for recursive action (with anti-forkbomb effect protection ;) ) + two self-finishing top commands!

IMPORTANT: Run the script_main.sh with 0 as argument!!! (otherwise you might get spammed by xterms indefinitely)
```
./script_main.sh 0
```

TODO: Make the xterms appear at random positions...

And here's the result:

---

### Post by mr_gourami on 2009-04-04
i am very new to ubuntu and the whole terminal usssage. i downloaded your .zip and followed the readme, or i believe i did to the best of my abilities. 

i still cant get anything to happen. this is the latest error message 

madison@Seahorse-Laptop:~$ /home/madison/Downloads/oo/script_main.sh 10
/home/madison/Downloads/oo/script_main.sh: line 59: txt_noun: No such file or directory
madison@Seahorse-Laptop:~$ 


also im not sure im doing the
chmod +x <file>
correctly. I did this and recieved no error message so i assume i did it correctly 
chmod +x <file> /home/madison/Downloads/oo/script_period_progress.sh
i only did that with the files ending in .sh that is correct?

---

### Post by KIAaze on 2009-04-04
You have to run the script from the "oo" directory where the text files containing the words used are located:
```
cd /home/madison/Downloads/oo/
./script_main.sh 10

```

And yes, only applying chmod to the .sh files (shellscripts) is correct:
```
chmod +x *.sh
```

---

### Post by Tom_OMG_X on 2010-12-24
> **KIAaze said:**
> Hi Tundro Walker,
I started implementing the stuff from ideas.txt. :)

Added files:
* whiptail_progressbar.sh: script to demonstrate the use of whiptail
* Operation_Overkill.py: [modification of the script created by blithen]("http://ubuntuforums.org/showthread.php?p=4974544#post4974544")
* boldtext.sh: bold text demo
* colors.sh: color demo
* oo.cfg: Operation Overkill configuration file! Here you can configure how many loops and with what probability each action runs.

Note: If you want all actions back again, uncomment the commented commands in eval_txt and change oo.cfg so that CASE_MIN=0 and CASE_MAX=100.
I hope the rest is self-explanatory.
If you have any questions, just ask.

Modified files:
* script_main.sh: implemented usage instructions (run without arguments to see them) + use of oo.cfg
* script_random_generator.sh: Fixed it so that it also works for numbers between 0 and 1 for example
* txt_evals: Added the new scripts I created in there + ./script_main itself for recursive action (with anti-forkbomb effect protection ;) ) + two self-finishing top commands!

IMPORTANT: Run the script_main.sh with 0 as argument!!! (otherwise you might get spammed by xterms indefinitely)
```
./script_main.sh 0
```

TODO: Make the xterms appear at random positions...

And here's the result:
hey i get this and it stops is that normal?

./script_main.sh: line 308: festival: command not found

---

### Post by KIAaze on 2010-12-25
> **Tom_OMG_X said:**
> hey i get this and it stops is that normal?

./script_main.sh: line 308: festival: command not found

Install festival (a text to speech synthesis program):
```
sudo apt-get install festival
```

---

### Post by bredsaal on 2010-12-25
Hah, that's pretty funny. :-) Good work dude.

---

### Post by jackwilsdon on 2011-02-22
it wont run under mac osx, please fix it.
Error running script_main.sh
> ./script_main.sh 

./script_main.sh: line 143: ((: i <  : syntax error: operand expected (error token is " ")


---

### Post by jackwilsdon on 2011-02-22
Problems :S on osx:confused::confused::confused::confused::(
Piggy-backing Locked Email minus Cryptology!expr: syntax error
expr: syntax error
expr: non-numeric argument
./script_period_progress.sh: line 78: ((: < 5 : syntax error: operand expected (error token is "< 5 ")
expr: syntax error
expr: syntax error
expr: syntax error
./script_period_progress.sh: line 100: ((: i < - : syntax error: operand expected (error token is " ")
=P
Dumping Local Modem upon ARES Data-Dictionaryexpr: syntax error
expr: syntax error
expr: non-numeric argument
./script_period_progress.sh: line 78: ((: < 5 : syntax error: operand expected (error token is "< 5 ")
expr: syntax error
expr: syntax error
expr: syntax error
./script_period_progress.sh: line 100: ((: i < - : syntax error: operand expected (error token is " ")

expr: syntax error
expr: syntax error
expr: non-numeric argument
expr: syntax error
expr: syntax error
./script_period_progress.sh: line 100: ((: i <  : syntax error: operand expected (error token is " ")
X_X
Reload Measured Hardware under SIT-REP!...
Measure Ninja-able Response IPexpr: syntax error
expr: syntax error
expr: non-numeric argument
./script_period_progress.sh: line 78: ((: < 5 : syntax error: operand expected (error token is "< 5 ")
expr: syntax error
expr: syntax error
expr: syntax error
./script_period_progress.sh: line 100: ((: i < - : syntax error: operand expected (error token is " ")

expr: syntax error
expr: syntax error
expr: non-numeric argument
expr: syntax error
expr: syntax error
./script_period_progress.sh: line 100: ((: i <  : syntax error: operand expected (error token is " ")
END
xterm:  bad command line option "Global"

usage:  xterm [-/+132] [-C] [-Sccn] [-T string] [-/+ah] [-/+ai] [-/+aw]
    [-b number] [-/+bc] [-bcf milliseconds] [-bcn milliseconds] [-bd color]
    [-/+bdc] [-bg color] [-bw number] [-/+cb] [-cc classrange] [-/+cjk_width]
    [-class string] [-/+cm] [-/+cn] [-cr color] [-/+cu] [-/+dc]
    [-display displayname] [-e command args ...] [-fa pattern] [-fb fontname]
    [-/+fbb] [-/+fbx] [-fd pattern] [-fg color] [-fi fontname] [-fn fontname]
    [-fs size] [-fw fontname] [-fwb fontname] [-fx fontname] [%geom] [#geom]
    [-geometry geom] [-help] [-/+hm] [-/+hold] [-iconic] [-/+ie] [-/+im]
    [-into windowId] [-/+j] [-/+k8] [-kt keyboardtype] [-/+l] [-/+lc]
    [-lcc path] [-leftbar] [-lf filename] [-/+ls] [-/+maximized] [-/+mb]
    [-mc milliseconds] [-/+mesg] [-/+mk_width] [-ms color] [-n string]
    [-name string] [-nb number] [-/+nul] [-/+pc] [-/+pob] [-rightbar] [-/+rv]
    [-/+rvc] [-/+rw] [-/+s] [-/+samename] [-/+sb] [-selbg color] [-selfg color]
    [-/+sf] [-/+si] [-/+sk] [-sl number] [-/+sm] [-/+sp] [-/+t] [-ti termid]
    [-title string] [-tm string] [-tn name] [-/+u8] [-/+uc] [-/+ulc] [-/+ulit]
    [-/+ut] [-/+vb] [-version] [-/+wc] [-/+wf] [-xrm resourcestring]
    [-ziconbeep percent]

Type xterm -help for a full description.


/var/log/dpd.log:Waiting for ACPI device and SMC to exist before host is ready.
/var/log/dpd.log:ACPI device does not exist yet.
/var/log/dpd.log:Failed to find ACPI device and/or SMC after timer expired. Exit!
/var/log/fuse-ext2_util.log:2011-01-31 20:06:35: [Mount] Got plain device "/dev/disk1s1"
/var/log/fuse-ext2_util.log:2011-01-31 20:06:35: [Mount] Got raw device "/dev/rdisk1s1"
/var/log/fuse-ext2_util.log:2011-01-31 20:06:48: [Mount] Got plain device "/dev/disk1s2"
/var/log/fuse-ext2_util.log:2011-01-31 20:06:48: [Mount] Got raw device "/dev/rdisk1s2"
/var/log/install.log:Feb 22 10:30:00 device-442bf4 newsyslog[41633]: logfile turned over due to size>1000K
/var/log/kernel.log:Feb 19 20:09:41 Jack-Wilsdons-MacBook-Pro-15 kernel[0]: The USB device Apple Internal Keyboard / Trackpad (Port 2 of Hub at 0x1d000000) may have caused a wake by issuing a remote wakeup (2)

---

