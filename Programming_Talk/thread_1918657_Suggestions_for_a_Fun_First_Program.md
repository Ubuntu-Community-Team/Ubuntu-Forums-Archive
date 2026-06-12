---
title: "Suggestions for a Fun First Program"
date: 2012-02-01
forum: Programming Talk
---

### Post by hwttdz on 2012-02-01
A friend is possibly interested in trying to program something and I'm looking for something just beyond hello world (which you have to admit isn't very "fun"), that would be entertaining and instructive.  Language will probably be perl (but I speak c/fortran/bash/maybe java).  A first thought was a shakespearian insult generator i.e. three sets of words it picks a word at random from each set and spits out an insult.  I suppose I could make it a little more politically correct and do a complement generator instead.  I think even tic-tac-toe is probably complicated for a first go.  Any other ideas.  Thanks.

---

### Post by JDShu on 2012-02-01
My first significant-ish program was Tetris, which I learned a great deal from.

---

### Post by Hetepeperfan on 2012-02-01
Hi

What I found really fun was a wordscramble program, I also used this program to learn C a few years back. It could read a textfile from stdin.
It had a loop:
```
while ( (c = getchar()) != EOF ) {
/*get a word, scamble it, print it to stdout and continue with the next word. oh and don't forget to print all non word characters. in the proper place.*/
}

```so I needed to create my own functions to scramble a bit in a cstring. learn ctype.h to find out whether a char was whitespace, interpunction or something to scramble. Of course the first and the last letter of each remained the same so the words would remain readable.
A bonus was that I could scramble the word document that contained my master thesis for university. If I did this on linux MS word was actually able to display a readable but it didn't work in windows with MINGW (I never found out why actually).

example output below.

Maarten

Hi

Waht I found rllaey fun was a wcbomldrsare pgrarom, I aslo used tihs prrgaom to lrean C a few yreas bcak. It cluod raed a tfixlete form stdin.
It had a loop:
```
while ( (c = gcatehr()) != EOF ) {
/*get a word, slcambe it, print it to sodutt and coninute wtih the nxet word. oh and don't forget to pinrt all non wrod ccarhtares. in the poerpr pacle.*/
}

```so I neeedd to craete my own fonctinus to sraclmbe a bit in a citsnrg. laern ctype.h to fnid out wehtehr a cahr was waptsecihe, iionrctutenpn or smhnitoeg to sarcblme. Of crsuoe the fsirt and the last ltteer of ecah riamened the smae so the wdors wolud rmiaen raealbde.
A buons was taht I cuold sbalrmce the word doncuemt taht caietonnd my msater thseis for uistnreviy. If I did tihs on lnuix MS word was acutally albe to dspliay a rdaeblae but it didn't wrok in wdinwos wtih MINGW (I neevr found out why alcualty).

epmlaxe optuut below.

Maetran

---

### Post by Bodsda on 2012-02-02
My first program in any language is always a guess the number game.

---

### Post by Tony Flury on 2012-02-02
If you want a challenge - you could try a Gui based calculator - gets you working with GUI toolkits/libraries - starts you thinking about stacks (if you do operator priority etc).

Or maybe an alarm clock - even a digital one with multipe programmable alarms.

---

