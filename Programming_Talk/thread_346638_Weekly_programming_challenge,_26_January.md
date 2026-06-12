---
title: "Weekly programming challenge, 26 January"
date: 2007-01-26
forum: Programming Talk
---

### Post by 56phil on 2007-01-26
Hi, everyone.  I have the responsibility of managing this weeks programming challenge.

This weeks challenge is open ended: you must create a program that plays the [Powerball]("http://www.powerball.com/index.asp") lottery.  You can make this task as simple or complicated as you like.  Please include some comments in your submission that explain you algorithm. You can use your favorite programming language. However, since Python is the quasi-official language of Ubuntu, I hope you will consider using it this week. The winning submission will be well thought out, lean, and probably include an analysis of past drawings.

---

### Post by Wybiral on 2007-01-26
Could you elaborate what exactly you mean by "plays the Powerball lottery"?
Generates the random numbers?

---

### Post by meng on 2007-01-26
My python suggestion, the first but not the best!
```

import random
whitetop, redtop = 55, 42 # highest numbered balls
whiteballs = range(1, whitetop + 1)
random.shuffle(whiteballs)
whitechosen = whiteballs[:5] # take first 5
whitechosen.sort()           # sort in ascending order
whitetuple = tuple(whitechosen)  # and then freeze as tuple (suggestions
                                 # for combining these 3 lines are welcome!)
redchosen = random.randint(1,redtop)
print "This week's draw:"
print "Red balls: %d %d %d %d %d" % whitetuple
print "Powerball: %d" % redchosen

```

It doesn't take into account the history of the game.

---

### Post by laxmanb on 2007-01-26
Really... just generate a few random numbers??

:/ 

not too challenging...

---

### Post by amo-ej1 on 2007-01-26
The main challenge is imo figuring out how that damn thing works ;)

---

### Post by public_void on 2007-01-26
I'm guessing 56phil means a game that simulates the powerball (lottery). So the user selects their numbers and the program generates the winning numbers and tells them if they have won and how much depending on [the powerball prizes](http://www.powerball.com/powerball/pb_prizes.asp). I could be wrong 56phil should clarify.

---

### Post by jblebrun on 2007-01-26
Ok, so I decided to make a little program that plays lots of powerball. It loops forever, doing two games at a time. One game is fixed, and always plays the same numbers. The other game picks new numbers every time. You run the program, and every 10000 games it tells you

Games #: <fixed win>, <fixed powerwin>, <rand win>, <rand powerwin>

Win means you matched the 5 "normal" numbers. 
Power win means you matched the 5 numbers and the powerball number.

The 5 "white" numbers are always unique, since according the Powerball website, they are all drawn from the same bin. But the Powerball number is drawn from its own bin, so it can be a repeat of one of the first 5 numbers. 

For something this intensive, it should really be done in C/C++ for maximal performance. But It's 3:30am, and I don't feel like writing in anything but Python. 

```

from random import shuffle,choice

class PowerBall:
    
    def __init__(self):
	bin=range(1,56)
	shuffle(bin)
	self.whiteballs=bin[0:5]
	self.whiteballs.sort()
	self.powerball=choice(xrange(1,42))

    def __str__(self):
	print self.whiteballs, self.powerball
	return "%s %s %s %s %s Powerball: %s"%(tuple(self.whiteballs)+(self.powerball,))

class PowerBallGame:
	
    def __init__(self, guess=None):
	self.guess=PowerBall()

    def play(self):
	pull=PowerBall()
	power=(pull.powerball==self.guess.powerball)
	win=(pull.whiteballs==self.guess.whiteballs)
	powerwin=win and power
	if win:
	    win=1
	if powerwin:
	    powerwin=1
	return win,powerwin

fixedgame=PowerBallGame()
games,fw,fpw,rw,rpw=0,0,0,0,0

while(1):
    if (games % 10000) == 0:
	print "Game %s: %s,%s,%s,%s"%(games,fw,fpw,rw,rpw)
    games+=1
    w,pw=fixedgame.play()
    fw+=w
    fpw+=pw 
	    
    w,pw = PowerBallGame().play()
    rw+=w
    rpw+=pw 
    

```

Mine's played 1.5 million games and no one has one yet. Not surprising, given the 1/417,451,320 chance of a normal win, and 1/17,532,955,440 of a powerball win.

---

### Post by jblebrun on 2007-01-26
Ok, here's the C version, which is  quite faster (the python version above could be made faster, but  it's a fun prototype)
```

//Just my own quick bubble sort cuz it's only 5
void sort(char num[]) {
    int i,j;
    for (i=4; i>=0; i--) 
	for (j=0; j<i; j++)
	    if(num[j+1]<num[j])
	    {
		int t=num[j+1];
		num[j+1]=num[j];
		num[j]=t;   
	    }        

}

void powerball(char* balls) {
    char* bin=calloc(55,sizeof(char));
    char i,pick;
    for(i=0; i<5; i++)
    {
	//Pick number not already marked as picked.
	do { 
	    pick=rand()%55+1;
	} while(bin[pick]!=0);
	balls[i]=pick;
	bin[pick]=1;
    }
    sort(balls);
    balls[5]=rand()%42+1;
    free(bin);
}

int check(char a[], char b[]) {
    int i;
    for(i=0; i<5; i++)
	if(a[i] != b[i])
	    return 0;
    if(a[5]==b[5])
	return 2;
    return 1;

}
int main(void) {
    char game[6];
    char fixed[6];
    char pull[6];
    int games=0,fw=0,fpw=0,rw=0,rpw=0;
    srand(time(0));
    powerball(fixed);
    while(1) {
	int w=0;
	if(!(games % 100000))
	    printf("Game %d: %d %d %d %d\n",games,fw,fpw,rw,rpw);
	powerball(game);
	powerball(pull);
	if(w=check(pull,game))
	    rw=w & 1; rpw=w & 2;
	if(w=check(pull,fixed))
	    fw=w & 1; fpw=w & 2;
	games++;
    }
}

```

---

### Post by 56phil on 2007-01-26
Clarification:

What I had in mind when I wrote the challenge was this. Write a program that simulates a person that plays the Powerball lottery.

The challenge, as I see it, comes from having the program get past drawing data off the Internet and using that data to guide the choices the program makes.

---

### Post by meng on 2007-01-26
Another entry that doesn't actually solve the problem. This program counts the number of times each ball has been drawn, based on the historical data.

```
winfile = open('winnums-text.txt', 'r')
winstrings = winfile.readlines()
redtop = 55
whitetop = 42
redcounts = [0] * redtop
whitecounts = [0] * whitetop
headerline = winstrings.pop(0) # garbage
for winstring in winstrings:
    winelements = winstring.split('  ')
    date = winelements.pop(0) # garbage
    for reds in range(5):
        redcounts[int(winelements.pop(0)) - 1] += 1
    whitecounts[int(winelements.pop(0)) - 1] += 1
print "Red Ball counts"
for inc in range(redtop):
    print "%2d: %3d     " % (inc + 1, redcounts[inc]),
    if inc % 4 == 3: print
print "\n\n\nPower Ball counts"
for inc in range(whitetop):
    print "%2d: %3d     " % (inc + 1, whitecounts[inc]),
    if inc % 4 == 3: print

```

The file can be downloaded here:
[http://www.powerball.com/powerball/winnums-text.txt](http://www.powerball.com/powerball/winnums-text.txt)
(too large for me to attach :()

---

### Post by ghostdog74 on 2007-01-26
A real challenge would be to predict the next winning number, based on historical data, using some statistical analysis or some advance maths or something..:D

---

### Post by 56phil on 2007-01-26
> **ghostdog74 said:**
> A real challenge would be to predict the next winning number, based on historical data, using some statistical analysis or some advance maths or something..:D

Yes! But the odds are very long. 

Meng has a good idea in doing the frequency count. There's a simple way to have the program open the page with the winning numbers using Python's urllib2 module. I'm hoping someone will use that technique. Additionally, you should not go back beyond August 31, 2005. That's because there was a rule change on that drawing.

---

### Post by Note360 on 2007-01-26
[http://www.powerball.com/powerball/pb_frequency.asp](http://www.powerball.com/powerball/pb_frequency.asp)
THat should help you. I am not sure if I am allowed to post it here, but wtvr. It is easy enough to find.

---

### Post by hod139 on 2007-01-26
> **ghostdog74 said:**
> A real challenge would be to predict the next winning number, based on historical data, using some statistical analysis or some advance maths or something..:D
If the balls are drawn truly uniformly randomly, then no amount of historical data, statistical analysis, advanced math, or something else will help.  This is because each trial is independent from a previous trial.  Think of flipping a coin, the probability of getting a head (H) on the ith trial does not change if you know the outcomes of all the previous trials.  For example, say you flip a coin 10 times, and on each outcome you got a heads:
HHHHHHHHHH
The probability of getting a H on the next flip is still 1/2.  You cannot think that a tails is going to be more likely just because you have seen 10 Heads.

Looking at the frequency can help confirm that the balls are following uniform distribution.  The only way the historical data will help is if there is an anomaly, say the number 5 ball is slightly smaller and gets selected slightly more often. Then this anomaly would show up in the history.

---

### Post by meng on 2007-01-26
Okay, we'll play it your way and use urllib2. Also, the program now calculates the most common draws.
```

import urllib2
address = 'http://www.powerball.com/powerball/winnums-text.txt'
winstrings = urllib2.urlopen(address).readlines()
redtop = 55
whitetop = 42
lastdate = '08/31/2005'
redcounts = [0] * redtop
whitecounts = [0] * whitetop
headerline = winstrings.pop(0) # garbage
for winstring in winstrings:
    winelements = winstring.split('  ')
    date = winelements.pop(0) # garbage
    for reds in range(5):
        redcounts[int(winelements.pop(0)) - 1] += 1
    whitecounts[int(winelements.pop(0)) - 1] += 1
    if date == lastdate: break
pairedreds = zip(range(1, redtop + 1), redcounts)
pairedwhites = zip(range(1, whitetop + 1), whitecounts)
print "Red Ball counts"
for reds in pairedreds:
    print "%2d:%3d     " % reds,
    if not (reds[0] % 4): print
print "\n\n\nPower Ball counts"
for whites in pairedwhites:
    print "%2d:%3d     " % whites,
    if not (whites[0] % 4 ): print
# Now to choose the most commonly drawn numbers
# At least as many as need to be drawn
def chooseMaxes(pairedlist, numtochoose):
    if numtochoose >= len(pairedlist): return pairedlist # can't choose more numbers than choices
    maxlist = []
    modalfreq = max(x[1] for x in pairedlist)
    while True:
        maxlist.extend(x[0] for x in pairedlist if x[1] == modalfreq)
        if len(maxlist) >= numtochoose: return maxlist
        modalfreq -= 1
print "\n\n\nMost common red balls chosen were:",
print str(chooseMaxes(pairedreds, 5))[1:-1]
print "Most common power balls chosen were:",
print str(chooseMaxes(pairedwhites, 1))[1:-1]

```

---

### Post by jblebrun on 2007-01-26
```

from pylab import *

f=open('pb.txt', 'r')
redcount=[0]*43
whitecount=[0]*56
f.readline()
for i in f.readlines():
    i=i.rstrip("\n")
    vals=i.split("  ")	
    for w in vals[1:6]:
	whitecount[int(w)]+=1
    redcount[int(vals[6])]+=1
plot(redcount,'r')
plot(whitecount,'k')
xlabel('Number')
ylabel('Number of draws')
legend(("Powerball","Regular Ball"))
savefig('pulls.png')

```

Here's the result:
[IMG]http://jasonlebrun.info/files/pulls.png[/IMG]

It looks like some statistical analysis could be useful.

---

### Post by Lux Perpetua on 2007-01-26
> **56phil said:**
> Clarification:

What I had in mind when I wrote the challenge was this. Write a program that simulates a person that plays the Powerball lottery.

The challenge, as I see it, comes from having the program get past drawing data off the Internet and using that data to guide the choices the program makes.
In that case, here is my C program:

```
[font="Courier New"]int main(void) {
    return 0;
}[/font]
```That's right, it doesn't do anything. The best way to play a lottery is not to play at all.

---

### Post by 56phil on 2007-01-26
> **Lux Perpetua said:**
> In that case, here is my C program:

```
[font="Courier New"]int main(void) {
    return 0;
}[/font]
```That's right, it doesn't do anything. The best way to play a lottery is not to play at all.

lol Have you been talking to my wife?

---

### Post by lnostdal on 2007-01-26
> **56phil said:**
> lol Have you been talking to my wife?

Smart wife :)

---

### Post by Wybiral on 2007-01-26
> **lnostdal said:**
> Smart wife :)

Indeed... Statistics will only get you so far with RANDOM numbers, if anywhere... Keep in mind the concept of RANDOM. About the only thing math can do for you in this case is estimate the probability of winning, but that doesn't really help.

---

### Post by hod139 on 2007-01-26
> **Wybiral said:**
> Indeed... Statistics will only get you so far with RANDOM numbers, if anywhere... Keep in mind the concept of RANDOM. About the only thing math can do for you in this case is estimate the probability of winning, but that doesn't really help.

Just shouting RANDOM and saying that math can't do anything for you is not really correct.  If what you meant to shout was UNIFORM RANDOM, then math can't really help you predict the outcome.  For a concrete example, look back at my earlier coin flipping post.  With a fair coin the past history cannot hep you determine if the next flip will be a heads or tails, since each flip is conditionally independent of previous flips.  The probability of getting a heads is always 1/2.  

However, what if I told you the coin was unfair, that is it will favor flipping heads or tails.  Each trial is still RANDOM, but now with the extra information of an unfair coin math can do something for you; you can use the history to determine the bias (either heads or tails).  Once you know the bias, you can guess that the coin will land on its preferred side and more often than not (probability > 1/2) you will be correct.  More technically, your expected payoff is now > 0.

If you are going to start shouting at someone, you best make sure you completely know what you are talking about!

---

### Post by Wybiral on 2007-01-26
Well, unless you are saying that the lottery is rigged or that there is a statistical pattern, then it is "uniformly random"

But I think if people knew about this statistical pattern, then it wouldn't be much of a lottery.

I wasn't shouting, I was just emphasizing on the fact that something as random as some balls being blown around, unless you have some proof of uneven weight on the balls and some kind of obvious statistical increase, your odds will always be the same, not matter what numbers you guess, so it would simply be random.

---

### Post by hod139 on 2007-01-26
> **Wybiral said:**
> Well, unless you are saying that the lottery is rigged or that there is a statistical pattern, then it is "uniformly random"

The lottery releases the past results just to prove that it isn't rigged.  You never said uniformly random in your first post, only random.  There is a difference.

> 
I wasn't shouting
Oh really??
> 
Keep in mind the concept of RANDOM
> 
I was just emphasizing
Looked like shouting too me, which is why I responded somewhat harshly.

> 
 on the fact that something as random as some balls being blown around, unless you have some proof of uneven weight on the balls and some kind of obvious statistical increase, your odds will always be the same, not matter what numbers you guess, so it would simply be random.
The proof of uniformity comes from the history released by the lottery.  This is why they release the data, so people can trust that the balls are chosen uniformly randomly.  There is no such thing as simply random.  Just because you have a set of random events does not mean the outcome of each event is equally likely.  This is where you are getting confused.  Think of my biased coin example.  If I tell you that the probability of getting heads is 99%, then we no longer have a uniform random distribution.  Each random event (heads or tails) is possible, just not equally likely.

I think you understand the concept, just make sure you are more precise if you are going to shout, or emphasize, it to other people.  Telling people that it is random and therefore math cannot help was just wrong.  It's the **uniform** randomness that makes the predictions of the outcome impossible, not the randomness.

---

### Post by Wybiral on 2007-01-26
Well, I understand that nothing is exactly random... Computer generated random numbers for instance, aren't *random* they have to come from somewhere, and that path is derived from some sort of algorithm which is by all means not RANDOM. I was emphasizing random in terms of unpredictability... Since you have no control or ability to predict the way the balls are placed in or the exact millisecond of time that they are blown around and released... It isn't truly random, but it is most likely unpredictable... I guess thats all I meant by random, unpredictable.

In the true literal definition of the word, nothing is RANDOM, just unpredictable.

---

### Post by hod139 on 2007-01-26
I guess I gave you more credit than you deserved, you really don't understand probability.  The concept of a random event is very well defined.   Look up probability theory or measure theory.

The random number *generators* in computers only generate pseudo-random sequences, however you can use advanced algorithms like the mersenne-twister which will produce sequences longer than the computer can detect.

---

### Post by Wybiral on 2007-01-26
Ok, please... Enlighten me. Im not being sarcastic, PM me if you want... I'm curious what you mean by probability in this issue.

---

### Post by Note360 on 2007-01-26
Look, ok the probability that a number will fall is always 1/the number of balls. YOu cant change it unless you add in another ball. Just because a number shows up more often than another doesnt change the probability of that number showing up. This is exactly the same as some one else said. Ok, now if we wanted to add together to see the probability of a number AND another number then it would look like this.

1/number of balls + 1/(number of balls-1)

I may be wrong

---

### Post by hod139 on 2007-01-26
> **Note360 said:**
> Look, ok the probability that a number will fall is always 1/the number of balls. YOu cant change it unless you add in another ball. Just because a number shows up more often than another doesnt change the probability of that number showing up. This is exactly the same as some one else said. Ok, now if we wanted to add together to see the probability of a number AND another number then it would look like this.

1/number of balls + 1/(number of balls-1)

I may be wrong

Again, this reasoning assumes that each draw is conditionally independent of previous draws and that each ball is equally likely to be drawn, or you are drawing **uniform** samples.  Image this scenario: there are 10 balls.  9 of them are made of coal and one is made of diamond.  You then tell someone to draw one ball randomly.  Do you still think each ball has a 1 in 10 chance of being drawn?!

All I'm trying to do is be slightly more precise with these arguments on sampling/randomness.

> **Wybiral said:**
> Ok, please... Enlighten me. Im not being sarcastic, PM me if you want... I'm curious what you mean by probability in this issue.


I think I've detracted enough from this thread, so I will try and come up with some decent sources and pm this discussion with you later.

---

### Post by Wybiral on 2007-01-27
> **hod139 said:**
> ...I think I've detracted enough from this thread, so I will try and come up with some decent sources and pm this discussion with you later...

Ok, cool. Thanks.

---

### Post by jblebrun on 2007-01-27
> **Note360 said:**
> Look, ok the probability that a number will fall is always 1/the number of balls. YOu cant change it unless you add in another ball. Just because a number shows up more often than another doesnt change the probability of that number showing up. This is exactly the same as some one else said. Ok, now if we wanted to add together to see the probability of a number AND another number then it would look like this.

1/number of balls + 1/(number of balls-1)

I may be wrong

Yes, this is wrong. 

To find the probability of N independent events occuring, you multiply the probability of each event. For example, the probability of pulling 48 and 56 in two pulls out of a bin of 100 balls is:
1/100 * 1/99. 

if you add the probabilities, that tells you the probability of one of TWO numbers occurs for a given event.
So the probability of choosing either 48 **or** 56  on the first pull is 1/100+1/100 = 1/50.

---

### Post by Wybiral on 2007-01-27
But unless there is an obviously weighted probability, and I don't think there is... All you will gain is just that... An even probability for each number... So you can't use those statistics to estimate the next winner. If you could... Everyone would use it and the lottery would have to change it's game.

I'm going to liken it to the Heisenberg uncertainty principle... Except, instead of particles, it's lottery balls... Even if you know the initial condition, you still couldn't estimate their outcome as a result of unknown factors.

I strongly suggest you read some of Heisenberg's work.
Here's an article from wikipedia: [http://en.wikipedia.org/wiki/Uncertainty_principle](http://en.wikipedia.org/wiki/Uncertainty_principle)
I know it doesn't directly apply, but it seems relevant.

Also... You can't control or predict the initial condition (initial velocity/position/weight distribution of each ball), you can't control or predict the minute force differences each time from the fan blowing the balls... The small surface consistency's of each ball... And the exact interval of release of each ball (so, the duration that the above condition is applied).

All you have to go by is past statistics with no estimate the margin of error... And on top of that, not enough samples to tell if any trends are just coincidental.

I think you can try to use statistics... But I can't see it helping that much.

One more thing... Even if a number ends up being more probably, the order that they come out will be nearly impossible to find a trend for.

---

### Post by jblebrun on 2007-01-27
> **Wybiral said:**
> But unless there is an obviously weighted probability, and I don't think there is... All you will gain is just that... An even probability for each number... So you can't use those statistics to estimate the next winner. If you could... Everyone would use it and the lottery would have to change it's game.

I'm going to liken it to the Heisenberg uncertainty principle... Except, instead of particles, it's lottery balls... Even if you know the initial condition, you still couldn't estimate their outcome as a result of unknown factors.

I strongly suggest you read some of Heisenberg's work.
Here's an article from wikipedia: [http://en.wikipedia.org/wiki/Uncertainty_principle](http://en.wikipedia.org/wiki/Uncertainty_principle)
I know it doesn't directly apply, but it seems relevant.

Also... You can't control or predict the initial condition (initial velocity/position/weight distribution of each ball), you can't control or predict the minute force differences each time from the fan blowing the balls... The small surface consistency's of each ball... And the exact interval of release of each ball (so, the duration that the above condition is applied).

All you have to go by is past statistics with no estimate the margin of error... And on top of that, not enough samples to tell if any trends are just coincidental.

I think you can try to use statistics... But I can't see it helping that much.

Statistics has nothing to do with detecting calculating  the initial and subsequent positions of the lottery balls in the bin. That would be a solution based on analytical physics. 

All the Heisenberg uncertainty principle says is that you can not have infinitely accurate measurement of both velocity and position of a particle, because measuring the position of a particle will affect its velocity, and vice-versa. That has NOTHING to do with statistical inferences based on history or generalized system properties. 

The Heisenberg doesn't prevent you from saying something like "The 22 ball has more ink on it than the 1 ball, so it's just a little heavier." Now, obviously, the difference in draws caused by this discrepancy is not going to have much influence on your game, but nothing prevents you from making this statement. 

So, I agree with you: reading about Heisenber's work is definitely a good idea. However, it has nothing to do with this discussion of statistucs. 

I also agree that statistical inferences are going to be essentially useless here. However, the information you've presented to make that argument is misleading.

---

### Post by Wybiral on 2007-01-27
I know that most of it doesn't apply directly, I was just trying to highlight exactly how many uncertain factors are involved. I also pointed out that even if 22 has more weight, that isn't going to help you estimate which order they fall out, maybe the fact that it is more likely to be one of the numbers.

You might be able to narrow it down to a smaller selection of numbers... But probably not close enough to help a great deal.

Also, the Heisenberg thing was just a random fact... I know it isn't REALLY relevant here, but I thought it was an interesting chance to gain some interest in quantum physics.

Thats all, not that it wouldn't be pretty sweet if someone found a way to cheat the lottery... But you certainly wouldn't be the first person who has tried.

---

### Post by jblebrun on 2007-01-27
> **Wybiral said:**
> I know that most of it doesn't apply directly, I was just trying to highlight exactly how many uncertain factors are involved. I also pointed out that even if 22 has more weight, that isn't going to help you estimate which order they fall out, maybe the fact that it is more likely to be one of the numbers.


Order is not important for PowerBall lottery games. Even if it was, the weight of the ball **would** change the probability of a certain ball coming up within the first 5, which would change the way you should pick numbers... just by less (and it's already insignificantly small to begin with, so it's splitting split hairs... LOL). 

Consider a game where you draw only 2 balls, and order IS important. If ball 17 is lighter, then there is a SLIGHTLY higher chance of 
17 * 
* 17
being drawn, so you've still deviated from a perfectly uniform distribution of likelihood of picks.

> 
Also, the Heisenberg thing was just a random fact... I know it isn't REALLY relevant here, but I thought it was an interesting chance to gain some interest in quantum physics.


It's definitely something everyone should be familiar with!

---

### Post by Rui Pais on 2007-01-27
> **Wybiral said:**
> Ok, please... Enlighten me. Im not being sarcastic, PM me if you want... I'm curious what you mean by probability in this issue.

hi, you could give an eye on the very classical "Numerical Receipts" it have an introductory text thats is accessible and even funny and provide good algorithms (in C and fortran) for random numbers. [Here is the link]("http://www.nrbook.com/b/bookcpdf.php"). Check chapter 7.

---

### Post by hk_2999 on 2007-01-29
Okay, can anyone help me, I don't get this.

I'm making my own entry into the challenge, it's pretty complicated(with past draw and probable combination analysis) and its my idea of learning and practicing C++, and I have to know what this means so that I could program my game history and winning distribution code properly.

> 
Whenever the Powerball jackpot reaches a record level, the amount of the jackpot prize is limited to increases for each draw of no more than $25 million. The prize money collected in excess of the maximum $25 million increase, will be placed into the Match 5 Bonus prize pool and will accumulate until there is a jackpot winner. When there is a jackpot winner, the Match 5 Bonus prize pool will be divided equally among all winners of the Match 5 prize. The prize will be paid in one cash lump sum.

How much is the record level? Can anyone clarify me on how the Powerball jack pot grows and what size it starts in? What if there is no Match 4+red winner, does the bonus prize stay until the next draw?

Thanks in advance!

---

### Post by 56phil on 2007-01-29
The record level is in excess of $254,000,000. The exact amount escapes me right now.

The amount the jackpot increases is a function of participation. It starts at $15,000,000

I *think so*, but I'm not sure.

hope this helps

---

### Post by jblebrun on 2007-01-29
> **56phil said:**
> The record level is in excess of $254,000,000. The exact amount escapes me right now.

The amount the jackpot increases is a function of participation. It starts at $15,000,000

I *think so*, but I'm not sure.

hope this helps

There are much higher-probability ways of earning that amount of money. Of course, they take a bit more work, or might get you thrown in jail ;-)

---

### Post by hk_2999 on 2007-01-29
> **56phil said:**
> The record level is in excess of $254,000,000. The exact amount escapes me right now.

The amount the jackpot increases is a function of participation. It starts at $15,000,000

I *think so*, but I'm not sure.

hope this helps

Thanks! I'll just use that data now as default, it can be changed anyway anytime anyone wants it to.

Btw. How much $ is added to the jackpot whenever it is not won?

> 
There are much higher-probability ways of earning that amount of money. Of course, they take a bit more work, or might get you thrown in jail 

Yes. But lottery gives the most returns over the least time investment, and jail is so great a  time investment and you cant even use the money you worked so hard for.

---

### Post by meng on 2007-01-30
So ... basically no one's going to bother solving the problem, eh?

---

### Post by hk_2999 on 2007-01-30
solve what problem?

it's just a game system with built-in analysis and import/export data from features isnt it?

---

### Post by mvaniersel on 2007-01-30
It doesn't seem like there is much of an intellectual challenge here.

---

### Post by hk_2999 on 2007-01-30
The challenge seems to be finding out how the whole thing works, and being diligent enough to program it. Anyway, i'm practicing my knowledge of c++ to see if it can fit in to practical random challenge applications such as this, so it still looks good to me.

I've done so far:
> #include <iostream>
#include <vector>
#include <string>
#include <cstdlib>
#include <fstream>
#include <ctime> 
using namespace std;

// white and red ball max # value
#define W_MAX 55
#define R_MAX 42

////////////////////////////////////////////////////////////////////////////
// Classes
struct Ticket{ // encapsulates char[7] so that a wont point to another char* pointer
	char a[7]; // the last digit is the power play value
	operator char*(){return a;}
};

struct Player{
	string name;
	vector<Ticket> tickets;
	unsigned getWinAmt();
};

struct PowerBall{
	vector<Player> players;
	vector<Player> playersglobal;//does not list lost tickets
	vector<Ticket> drawhistory;
	unsigned int jackpot;
	unsigned int ticketsboughtglobal;
	
	vector<Player> draw();
	void saveToFile(char* file);
	void loadFromFile(char* file);
        void reset();

private:
	unsigned prize(unsigned);
	void writePlayer(Player a, ofstream& b);
        void readPlayer(Player a, ifstream& b);
};
////////////////////////////////////////////////////////////////////////////
// GUI stuff
void main_menu();
void addplayers();
void analysis();
void history();
void clear_history();
void draw();

////////////////////////////////////////////////////////////////////////////
// Main Functions
PowerBall gpbe; // global power ball engine
int main(){
	char u;// user choice

	gpbe.loadFromFile("powerdata");
	while(u!='q'){
		main_menu();
		cin >> u;
		switch(u){
			case '1': addplayers();break;
			case '2': draw();break;
			case '3': analysis();break;
			case '4': history();break;
			case '5': clear_history();break;
		}
	}
        gpbe.saveToFile("powerdata");
}
	
////////////////////////////////////////////////////////////////////////////
// Main Menu
void main_menu(){
	cout<<
	endl<<"Welcome to the GNU PowerBall emulator,"<<
	endl<<"What do you want to do?"<<
	endl<<"1. Add Players"<<
	endl<<"2. Draw"<<
	endl<<"3. Lottery Analysis"<<//beta1
	endl<<"4. Past Winners"<<
	endl<<"5. Clear History"<<
	endl<<"q. Quit"<<endl;
}


/*************/
// Algorithm //
///////////////

////////////////////////////////////////////////////////////////////////////
// each ball no. is drawn only once, a simple random generator is used instead of a real ball drum emulator
vector<Player> PowerBall::draw(){
	vector<Player> p;
	Ticket w,x;
	unsigned int i,j,k,l,m;

	//draw
	srand((unsigned)time(0));
	for(i=0;i<5;i++){
		draw:
		w[i]=(rand()%(W_MAX))+1;
		for(j=0;j<i;j++){
			if(w[j]==w[i])
			goto draw;
			}
		};
	w[5]=(rand()%R_MAX)+1;

	//check winners
	for(i=0;i<players.size();i++){
		for(j=0;players.at(i).tickets.size();j++){
			l=0;
			// see how many white balls hit(in any order)
			for(x[0]=0;k<5;k++){
				for(m=0;m<5;m++)
					if(players.at(i).tickets.at(j)[k]=w[m])l++;
			if(w[6]==players.at(i).tickets.at(j)[6])l+=6;
			
			//determine prize and change his last ticket entry to the prize he won
			l=prize(l);
			memcpy(x,&l,4);
			players.at(i).tickets.push_back(x);
			}
		}
	}
	//clear players
	players.clear();
	
	//add game to the draw history
	drawhistory.push_back(w);
}

unsigned PowerBall::prize(unsigned l){
	if(l==5)return 200000;
	if(l==6)return 3;
	if(l==7)return 4;
	if(l==8)return 7;
	if(l==9||l==4)return 100;
	if(l==10)return 10000;
	if(l==16)return jackpot;
	return 0;
}

void PowerBall::saveToFile(char* file){
	size_t i;
        ofstream myFile(file, ios::out | ios::binary);
        
        if(!myFile.fail()){
            i=players.size();
            myFile.write((char*)&i,sizeof(size_t));
            for(i=0;i<players.size();i++)
                writePlayer(players[i], myFile);
            i=playersglobal.size();
            myFile.write((char*)&i,sizeof(size_t));
            for(i=0;i<playersglobal.size();i++)
                writePlayer(playersglobal[i], myFile);
            i=players.size();
            myFile.write((char*)&i, sizeof(size_t));
            for(int i=0;i<drawhistory.size();i++)
                myFile.write(drawhistory.at(i),7);
            myFile<<jackpot<<ticketsboughtglobal;
        }
}

void PowerBall::loadFromFile(char* f ile){
	size_t i;
        Player j;
        Ticket k;
        ifstream myFile("data.bin", ios::in | ios::binary);
        
        if(!myFile.fail()){
            myFile.read((char*)&i,sizeof(size_t));
            players.reserve(i);
            for(i=0;i<players.size();i++){
                readPlayer(j, myFile);
                players.push_back(j);
            }
            myFile.read((char*)&i,sizeof(size_t));
            playersglobal.reserve(i);
            for(i=0;i<playersglobal.size();i++){
                readPlayer(j, myFile);
                players.push_back(j);
            }
            for(int i=0;i<drawhistory.size();i++){
                myFile.read((char*)&k,7);
                drawhistory.push_back(k);
            }
            myFile>>jackpot>>ticketsboughtglobal;
        }else reset();
}

void PowerBall::writePlayer(Player a, ofstream& b){
	b<<a.name;
	for(int i=0;i<a.tickets.size();i++)
            b.write(a.tickets.at(i),7);
}

void PowerBall::readPlayer(Player a, ifstream& b){
	Ticket c;
    
        b>>a.name;
	for(int i=0;i<a.tickets.size();i++){
            b.read(c,7);
            a.tickets.push_back(c);
        }
}

void PowerBall::reset(){
        drawhistory.clear();
        jackpot=1000000;
        players.clear();
        playersglobal.clear();
        ticketsboughtglobal=0;
}

unsigned Player::getWinAmt(){
        return (unsigned)tickets.back()[0];
}



---

### Post by eteran on 2007-01-30
Here is my "solution" in Ook!*

[http://phpfi.com/198804](http://phpfi.com/198804)

* Whats Ook!? [http://www.dangermouse.net/esoteric/ook.html](http://www.dangermouse.net/esoteric/ook.html)
* Interpreter for Ook! in Python: [http://www.pvv.ntnu.no/~oyving/code/python/pook.py](http://www.pvv.ntnu.no/~oyving/code/python/pook.py) (erase out the copyright comment line if it throws an error)

---

### Post by jblebrun on 2007-01-30
> **hk_2999 said:**
> The challenge seems to be finding out how the whole thing works, and being diligent enough to program it. Anyway, i'm practicing my knowledge of c++ to see if it can fit in to practical random challenge applications such as this, so it still looks good to me.

I've done so far:

Ack! Use code tags!

---

### Post by 56phil on 2007-01-31
Don't worry. I'm not going to declare myself the winner. Here's something I put together to demonstrate what I had in mind. ```

#!/usr/bin/python


""" Throws $5 at the powerball drawing using drawing data since 2005-08-31

This script accesses the past winning numbers from the powerball site
and creates a $5 ticket. """


import datetime, random, urllib2


def print_plays(a):
    """ prints a nx6 tuple of intigers 

    return None """
    PBFS = '%3d' * 5 + ' |' + '%3d'
    now_str = datetime.datetime.now().isoformat().split('T')
    print '\n', now_str[0].center(20), '\n'
    for play in a:
        print PBFS % play


def play_5():
    """ Plays the Powerball lottery five times

    The first play is random. The next two plays use balls with the
    lowest ferquencies. The last two plays use the balls with the
    highest frequencies.

    Frequency counts come from a list of previous drawings on the web.

    return tuple """
    URL = 'http://www.powerball.com/powerball/winnums-text.txt'
    END_DATE = '08/31/2005'
    PARAMETERS = ((0,5,1,0), (5,10,1,1), (-6,-11,-1,-2), (-1,-6,-1,-1))
    MAX_BALL_W = 55
    MAX_BALL_R = 42
    BALL_NUMBERS = [j for j in range(1, 56)]

    count_wb = [0] * MAX_BALL_W
    count_rb = [0] * MAX_BALL_R

    pb_hist = urllib2.urlopen(URL)
    records = pb_hist.readlines()
    pb_hist.close()
    records.pop(0)                                      # get rid of the header
    for record in records:
        field = record.split()
        for j in range(1,6):
            count_wb[int(field[j])-1] += 1              # count each white ball
        count_rb[int(field[6])-1] += 1                  # count the powerball
        if field[0] == END_DATE:                        # stop if at 2005-08-31
            break
    del records

    sorted_wb = sorted(zip(count_wb,BALL_NUMBERS))      # 1combine counts with
    sorted_rb = sorted(zip(count_rb,BALL_NUMBERS))      # ball numbers and sort

    play = sorted(random.sample(range(1,56),5))         # pick the white balls
    play.append(random.randint(1,MAX_BALL_R))           # pick the powerball
    plays = [tuple(play)]                               # start a new list

    for p in PARAMETERS:
        play = sorted([sorted_wb[j][1] for j in range(p[0],p[1],p[2])])
        play.append(sorted_rb[p[3]][1])
        plays.append(tuple(play))

    return tuple(plays)


if __name__ == '__main__':
    print_plays(play_5())

## --- EOF ---

```

---

