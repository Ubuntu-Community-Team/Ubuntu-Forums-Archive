---
title: "[bash] Audio tagging issues from script/CLI"
date: 2011-02-28
forum: Programming Talk
---

### Post by Lord Rocket on 2011-02-28
Hi guys. Not quite sure if this is 'programming' really, but here seems to be the least inappropriate place to put this, so here goes...

Alright, I'm having some real problems getting a very simple bash script to work. Basically, all I want it to do is rip a CD using CD Paranoia and then encode the resulting files into FLACs (although I get the same problem using LAME). The problem is that it refuses to tag the file if I try to use your standard bash $VARIABLES in any way.

I've also tried something similar from the command line, with the same results.

Anyway, the bash file is full of lines that look like this:

```
SONGTITLE="blah blah whatever"\
flac -T "ARTIST=$1" -T "ALBUM=$2" -T "TITLE=$SONGTITLE" -T "TRACK=01" -o "01 $SONGTITLE.flac" track01*.wav
```

Real simple stuff, like I said, just a bunch of commands being invoked one after t'other with some CL parameters thrown into the mix. I figure once I get this sort of thing to work reliably I can try something more complicated.

Anyway, this creates tag-free files generally called " .flac". This isn't what I'd like to happen but I really don't see what's wrong with the above. I have tried looking for other people's scripts and looking at basic bash tutorials, but those haven't helped much (generally they're too simple or way over my head). I've also tried changing the quotation marks to both graves and inverted commas, changing where the quotes go, and removing the quotes entirely but to no avail. Entering the tags in manually (eg. -T "TITLE=I Deliberately Ran Over Your Dog" etc.) works just fine, but that's not really what I'm after.
Can anyone tell me what I'm doing wrong here?

And, yes I could use a GUI program instead, but I'm trying to teach myself a bit of bash. It isn't going very well.

---

### Post by DaithiF on 2011-02-28
there is a trailing '\' after the songtitle assignment -- this will have the effect of escaping the newline that follows and cause bash to treat this and the next flac line as a single line rather than 2 ... which in turn means that songtitle does not get set in the current shell environment.  so I would remove the trailing '\' character and try again.

---

### Post by Lord Rocket on 2011-02-28
That simple, huh. Thanks - it works now.

OK stupid question time: how come I can change variables on the command line in cases like "EDITOR=nano visudo" or "CFLAGS=-O3 -march=native" et cetera but I need to newline this stuff in this particular case? Seems arbitrary.

---

### Post by DaithiF on 2011-03-01
the only stupid question is the one that goes unasked :)

actually its a very good question.  As you point out its quite common to do something like:
var=somevalue somecommand

which has the effect of populating var with somevalue for the purposes of somecommand's execution environment, but has the happy result of not changing the current shell environment.  Which means you can do one-off updates to variables for the running a single command without affecting that variable for the rest of your script or interactive session

In your example you were basically doing:
SONGTITLE="xyz.mp3" flac  blah blah -o "$SONGTITLE" but yet SONGTITLE wasn't being populated as you expected.

A couple of excerpts from man bash explains whats going on:
Firstly this part -- which explains what I said above:
```
If  no  command  name  results, the variable assignments affect the
       current shell environment.  Otherwise, the variables are  added  to
       the  environment of the executed command and do not affect the cur&#8208;
       rent shell environment.

```
Secondly this part:
```
SIMPLE COMMAND EXPANSION
       When a simple command is executed, the shell performs the following
       expansions, assignments, and redirections, from left to right.

       1.     The words that the parser has marked as variable assignments
              (those  preceding  the  command  name)  and redirections are
              saved for later processing.

       2.     The words that are not variable assignments or  redirections
              are  expanded.   If  any  words  remain after expansion, the
              first word is taken to be the name of the  command  and  the
              remaining words are the arguments.

```
so, taking your line:
SONGTITLE="xyz.mp3" flac  blah blah -o "$SONGTITLE"
step 1: songtitle assigment gets saved for later processing
step 2: the non-variable assignment part (flac blah blah -o "$SONGTITLE") gets expanded 
see whats happenend?  SONGTITLE assignment has not yet been performed when the command gets expanded, so $SONGTITLE expands to nothing.

You can see this happening too in a simpler example:
```
test="xyz" echo "$test"

```-- nothing is output
```
test="xyz" eval "echo \$test"
xyz

```
in the second example we delay the expansion of $test until the echo command itself is being run, and by then test has indeed been set and so we get the result xyz being output.

so the conclusion is to be aware of (and wary of) the order in which variables get expanded vs. assigned.

---

