---
title: "Regex Batch Rename Files"
date: 2012-11-08
forum: Programming Talk
---

### Post by drmrgd on 2012-11-08
Maybe I'm a little burned out at the moment.  Or maybe it's just my lack of skill with regular expressions, but I can't find a more simple way to rename a whole bunch of files that look like this:

```
IonXpress_001_R_2012_10_25_11_13_26_user_PCC-155-20121025.CPSCv4.TestRun.M02030405.sims_run155-20121025.CPSCv4.TestRun.M02030405.TMAPmod.sims.basecaller.bam
```

The goal is to get them to just be the first two fields (field two increments like IonXpress_002, IonXpress_003).  I ended up just hacking together something ugly that works:

```
for f in *.bam; do name=$(echo "$f"| awk -F_ '{ OFS="_"; print $1, $2 }'); echo mv "$f" $name.bam; done
```

I'd like to use this as a learning experience and see what a better way to do this is.  Since I have the luxury of the center of the filename all being the same, I guess I could brute force it by using rename like this:

```
rename 's/_R_2012_10_25_11_13_26_user_PCC-155-20121025.CPSCv4.TestRun.M02030405.sims_run155-20121025.CPSCv4.TestRun.M02030405.TMAPmod.sims.basecaller//' IonXpress_0*
```

But that seems kind of ugly too.  How would one use a regular expression or parameter expansion (which I tried and couldn't figure out how to pick up the second field if I used '_' to match on) to do this?

---

### Post by Vaphell on 2012-11-08
```
rename -nv 's/([^_]+_[0-9]+).*/$1.bam/' *.bam
```

```
$ f=IonXpress_001_R_2012_10_25_11_13_26_user_PCC-155-20121025.CPSCv4.TestRun.M02030405.sims_run155-20121025.CPSCv4.TestRun.M02030405.TMAPmod.sims.basecaller.bam
$ n=${f/_/|}; n=${n%%_*}; echo ${n/|/_}.bam
IonXpress_001.bam
$ echo ${f:0:13}.bam
IonXpress_001.bam
```

---

### Post by papibe on 2012-11-08
Hi drmrgd.

Since the character "_" is like a separator and you want to use just the 1st and 2nd fields, you may convert the string to a bash list (or array).

For example:
```
$ name="IonXpress_001_R_2012_10_25_11_13_26_user_PCC-155-20121025.bam"

$ new=(${name//_/ })

$ echo ${new[0]}
IonXpress

$ echo ${new[1]}
001

$ echo ${new[0]}_${new[1]}
IonXpress_001
```
Hope it helps.
Regards.

---

### Post by drmrgd on 2012-11-08
> **Vaphell said:**
> ```
rename -nv 's/([^_]+_[0-9]+).*/$1.bam/' *.bam
```

```
$ f=IonXpress_001_R_2012_10_25_11_13_26_user_PCC-155-20121025.CPSCv4.TestRun.M02030405.sims_run155-20121025.CPSCv4.TestRun.M02030405.TMAPmod.sims.basecaller.bam
$ n=${f/_/|}; n=${n%%_*}; echo ${n/|/_}.bam
IonXpress_001.bam
$ echo ${f:0:13}.bam
IonXpress_001.bam
```

Thanks yet again Vaphell.  I see how the first one works fairly well.  I really think I need to pick up a book on regular expressions as that's pretty far from where I was when I tried it.

Example 2 is a bit of a dirty trick, no?  You're switching around the delimiters so that you can do a parameter expansion a little more easily, aren't you?  That's no less ugly than my examples ;)

The third one has me completely perplexed.  I've seen syntax that's similar in the past, but I don't know how to read it.  Can you point me in the right direction on how that works and how I can use it in future?

> 
Since the character "_" is like a separator and you want to use just the 1st and 2nd fields, you may convert the string to a bash list (or array).

Thank you as well papibe.  Your strategy is how I came up with the awk method I used above.  Pretty simple to read and understand for a script, but I'd prefer something that I can just bend to my will and run very quickly on the fly (I have a lot of these to work through at the moment)

---

### Post by Vaphell on 2012-11-08
expanding papibe's idea
you can use *read -a* to form an array using arbitrary delimiter
```
IFS=_ read -a array <<< "$f"
```

> Example 2 is a bit of a dirty trick, no? You're switching around the delimiters so that you can do a parameter expansion a little more easily, aren't you? That's no less ugly than my examples

yes, it is somewhat dirty and situational -  if you wanted to include more segments this would fall apart (or should i say would require additional replace first _ with something else, not too scalable). I had to 'hide' the first one for a moment to strip the rest. Parameter expansions know only 'longest' and 'shortest' (which is a shame) so tailoring the proper solution often requires being 'creative' ;-)
assuming fixed number of _ you can also use
```
$ echo ${f%_*_*_*_*_*_*_*_*_*}
IonXpress_001
```

> The third one has me completely perplexed. I've seen syntax that's similar in the past, but I don't know how to read it. Can you point me in the right direction on how that works and how I can use it in future?

substring( variable, starting_pos, length )
```
$ a=abcdef
$ echo ${a:2:2}
cd
```
of course this is very situational, because the format of filenames has to be very rigid for it to work

---

### Post by drmrgd on 2012-11-08
That's an interesting way to load up the array. Read is a very under utilized tool in my box.  I tried to bring up the man pages on it, but what I get doesn't seem to make sense to this, and I don't see any of the options that I know (like -p or -s).  If I run 'man read' I get this:

```
read - read from a file descriptor
```

Is this correct?  Where can I learn about the other options for read?

> Parameter expansions know only 'longest' and 'shortest' (which is a shame)...

That makes me feel a little better about not being able to figure out how to make it work.  I now see why you have to have an intermediate in there in order to get that solution to work.

As I was eating dinner the solution to the third method dawned on me.  So simple!  I should have gotten that right away.  That seems like a very handy way, though to trim something like this (I have hundreds of these that are named a very similar way and I really mainly need the "IonXpress_xxx" string for now.

Let's say - for the sake of argument - that I wanted more.  Let's say I wanted to add a string from the middle of the filename like "IonXpress_001_run155.bam" (let's also assume that number changes, since it would be easy enough to tack on if it were static).  In that case, would the best strategy be build an array like papibe suggested or grab a field in awk like I did:

```
for f in *.bam; do echo mv "$f" $(echo "$f" | awk -F_ '{ OFS="_"; print $1,$2,substr($12,0,6)}').bam; done
```

or is the a better way to do this?  Perhaps this gets to the point of being complicated enough for complex statements?

---

### Post by Vaphell on 2012-11-08
> hat makes me feel a little better about not being able to figure out how to make it work. I now see why you have to have an intermediate in there in order to get that solution to work.

[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)
all the mentioned operations are pretty basic. The biggest problem inhibiting the usefulness of parameter expansion is the pattern syntax. Patterns use the same rules as file globs. You can use ? = single char, * = any sequence, [group of chars] but there are no operators like *,+,?,(),{x,y} from regex realm. If expansion supported full blown regexes... oh man, it's really nice to dream ;-)
You can enable beefier pattern syntax that supports *,+,? with shopt -s extglob, but sadly it doesn't work with parameter expansion at all (only globs).


> Let's say - for the sake of argument - that I wanted more. Let's say I wanted to add a string from the middle of the filename like "IonXpress_001_run155.bam" (let's also assume that number changes, since it would be easy enough to tack on if it were static). In that case, would the best strategy be build an array like papibe suggested or grab a field in awk like I did:

```
for f in *.bam; do echo mv "$f" $(echo "$f" | awk -F_ '{ OFS="_"; print $1,$2,substr($12,0,6)}').bam; done
```

or is the a better way to do this? Perhaps this gets to the point of being complicated enough for complex statements?

yes, the array approach that emulates your awk is the only pure bash that is still somewhat usable.
i think *${f[0]}_${f[1]}_${f[11]:0:6}* would mirror your code
In this case any method using trimming and replacements while still possible, would cross the threshold of common sense long time ago.

---

### Post by drmrgd on 2012-11-08
Very helpful and informative!  I really like parameter expansion, and I would wholeheartedly agree that it would be fantastic if it were expanded to include regexes.  Then again, I guess that's what things like perl and awk are for.

> In this case any method using trimming and replacements while still possible, would cross the threshold of common sense long time ago.

With regard to my common sense, I'm not sure I have too much to talk about there :D

Thanks again for the wealth of knowledge, Vaphell!

---

