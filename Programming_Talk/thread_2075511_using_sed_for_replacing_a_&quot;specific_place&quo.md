---
title: "using sed for replacing a &quot;specific place&quot;, not a find and replace..."
date: 2012-10-24
forum: Programming Talk
---

### Post by aroustaei on 2012-10-24
I want to use sed for replacing a "very specific" place in a text file,
not for doing a "find and replace" of a pattern.

For example my file is:
---------------
name = john
surname = smith
tall = 187.12 cm
age = 34
---------------

I want to replace "187.12" with something and I know it's address:
third line, starting from column 8 to 14.

In general I want to replace the text in
line "n", beginning column "p" ending column "q"
of file with something else. How do I do that?

not insisting for sed, anything portable which works on bash is fine!

Thank you very much

---

### Post by steeldriver on 2012-10-24
You should be able to address just the nth line specifically e.g. to do *command *on line 3 only

```
sed '3*command*'
```This kind of addressing is most often seen in deletions like *sed '5d'* (delete fifth line) but can be applied to substitutions as well, so you could find a pattern in the 3rd line consisting of a group of any 7 characters followed by any further 7 characters and replace just the first group - something like

```
sed '3s/^\(.\{7\}\)\(.\{7\}\)/\1/' file
```If you don't mind giving up a bit of portability you can use GNU sed extensions to get rid of some of the escapes

```
sed -r '3s/^(.{7})(.{7})/\1/' file
```

---

### Post by Vaphell on 2012-10-24
if you want to work with a specific line which has the same context, eg 'tall =' you can also use ```
'**/^tall =/** s/.../.../'
``` to modify it. I'd argue that it's safer than expecting a line number.

I suggest looking into awk too, some classes of problems are pain in the a.. with sed (it's dumb and regexes are sometimes tedious to write correctly), while awk understands the structure of the text more and offers tons of convenience. Not saying that it will work better here in this case, but the more tools the better, one can choose appropriate tool to the task at hand.

---

### Post by steeldriver on 2012-10-24
Agreed - sed can rapidly end up looking like an explosion in a punctuation factory, especially when lots of escaping is required - hard to read and maintain

---

### Post by stylishpants on 2012-10-24
You can modify the characters at a particular index within a line like this:

```
bob@cob:~$ cat /tmp/file
name = john
surname = smith
tall = 187.12 cm
age = 34

bob@cob:~$ perl -pe 'if($.=="3"){substr($_,7,6,"ABCDEF");} ' /tmp/file
name = john
surname = smith
tall = ABCDEF cm
age = 34

```

Some explanation:
The variable named $. is the current line number.
The substr() function takes the following arguments:
[INDENT]substr EXPR,OFFSET,LENGTH,REPLACEMENT[/INDENT]
For more information, run "perldoc -f substr"
Perl's "-p" flag iterates through each line in the given input file, running the given code before printing the line. 
The variable named "$_" holds the contents of the current line.

---

### Post by drmrgd on 2012-10-24
> **stylishpants said:**
> You can modify the characters at a particular index within a line like this:

```
bob@cob:~$ cat /tmp/file
name = john
surname = smith
tall = 187.12 cm
age = 34

bob@cob:~$ perl -pe 'if($.=="3"){substr($_,7,6,"ABCDEF");} ' /tmp/file
name = john
surname = smith
tall = ABCDEF cm
age = 34

```

Some explanation:
The variable named $. is the current line number.
The substr() function takes the following arguments:
[INDENT]substr EXPR,OFFSET,LENGTH,REPLACEMENT[/INDENT]
For more information, run "perldoc -f substr"
Perl's "-p" flag iterates through each line in the given input file, running the given code before printing the line. 
The variable named "$_" holds the contents of the current line.

Hmmm...that's pretty convenient.  I going to keep that idea handy as I'm sure I can use something along those lines from time to time.  I'm working on learning Perl at the moment, but pretty far behind as I just can't find the time to focus on it (too many things going on at the moment!).

> 
Agreed - sed can rapidly end up looking like an explosion in a punctuation factory, especially when lots of escaping is required - hard to read and maintain

Ha!!!  So true.  I think that's why I've been so intimidated about learning sed!  Very funny!:)

---

### Post by Vaphell on 2012-10-24
perl to me is like awk on steroids, too bad it looks like a randomly generated sequence of characters when pushed to the limits ;-)

---

### Post by aroustaei on 2012-10-24
> **steeldriver said:**
> You should be able to address just the nth line specifically e.g. to do *command *on line 3 only

```
sed '3*command*'
```This kind of addressing is most often seen in deletions like *sed '5d'* (delete fifth line) but can be applied to substitutions as well, so you could find a pattern in the 3rd line consisting of a group of any 7 characters followed by any further 7 characters and replace just the first group - something like

```
sed '3s/^\(.\{7\}\)\(.\{7\}\)/\1/' file
```If you don't mind giving up a bit of portability you can use GNU sed extensions to get rid of some of the escapes

```
sed -r '3s/^(.{7})(.{7})/\1/' file
```

Thanks, this will work for me!


> **Vaphell said:**
> if you want to work with a specific line which has the same context, eg 'tall =' you can also use ```
'**/^tall =/** s/.../.../'
``` to modify it. I'd argue that it's safer than expecting a line number.

I suggest looking into awk too, some classes of problems are pain in the a.. with sed (it's dumb and regexes are sometimes tedious to write correctly), while awk understands the structure of the text more and offers tons of convenience. Not saying that it will work better here in this case, but the more tools the better, one can choose appropriate tool to the task at hand.

Agree using tall is than giving just a line. But problem is that I might have several lines like "tall = "

> **stylishpants said:**
> You can modify the characters at a particular index within a line like this:

```
bob@cob:~$ cat /tmp/file
name = john
surname = smith
tall = 187.12 cm
age = 34

bob@cob:~$ perl -pe 'if($.=="3"){substr($_,7,6,"ABCDEF");} ' /tmp/file
name = john
surname = smith
tall = ABCDEF cm
age = 34

```

Some explanation:
The variable named $. is the current line number.
The substr() function takes the following arguments:
[INDENT]substr EXPR,OFFSET,LENGTH,REPLACEMENT[/INDENT]
For more information, run "perldoc -f substr"
Perl's "-p" flag iterates through each line in the given input file, running the given code before printing the line. 
The variable named "$_" holds the contents of the current line.

Thanks a lot! I am also really interested to learn a bit of perl. You settled me at the start line :)

I would like to thank all!

---

### Post by drmrgd on 2012-10-25
> **Vaphell said:**
> perl to me is like awk on steroids, too bad it looks like a randomly generated sequence of characters when pushed to the limits ;-)

Indeed it is, which is why I've sort of started down the path of learning it instead of Python, which was my original goal.  Considering that Larry Wall invented it since there was some things he couldn't do with AWK, I guess the relationship makes sense.  

It can get just about as ugly as sed, though....you're right.  In fact, for a good laugh, check out the "Obfuscated Perl Contest", which I don't think is held anymore.  Here's an example of some winning code:

```
@P=split//,".URRUU\c8R";@d=split//,"\nrekcah xinU / lreP rehtona tsuJ";sub p{
@p{"r$p","u$p"}=(P,P);pipe"r$p","u$p";++$p;($q*=2)+=$f=!fork;map{$P=$P[$f^ord
($p{$_})&6];$p{$_}=/ ^$P/ix?$P:close$_}keys%p}p;p;p;p;p;map{$p{$_}=~/^[P.]/&&
close$_}%p;wait until$?;map{/^r/&&<$_>}%p;$_=$d[$q];sleep rand(2)if/\S/;print
```

:confused::confused::confused:

---

### Post by Vaphell on 2012-10-25
that's why i am not too motivated to get into perl. While it has serious advantages like native multiline operations, which need to be hacked hard in case of other tools, or a crapton of modules it's not very self-documenting. When too much logic is compressed into too few bytes you can get lost reading code you wrote just a month ago.
Not that i use python much since i went the road of quick and dirty hacking with bash et consortes, but i imagine it's relative verbosity lends itself better to maintaining code.

---

### Post by mevun on 2012-10-25
With respect to the various languages mentioned pretty much all of them can support one-liners.

Perl one-liners seem to be most mentioned in general, but python and ruby also support them.  There are python wrappers that "import" some common modules so that its one-liners can use those modules without import statements.

Anyway, since most of the newer dynamic languages support indexing into strings by character position, then any of them could work with just slight changes in syntax.

So, even though **sed** and **awk** are known for one-liners, the newer languages also support them and in my opinion are much easier to understand, particularly python or ruby over perl.  Perl is best-known for its one-liners because it is older than python and ruby.  In fact, ruby is not even mentioned in the wiki [article]("http://en.wikipedia.org/wiki/One-liner_program") for one-liners.

---

