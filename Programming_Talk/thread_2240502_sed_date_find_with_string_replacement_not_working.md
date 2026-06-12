---
title: "sed date find with string replacement not working"
date: 2014-08-20
forum: Programming Talk
---

### Post by getut2 on 2014-08-20
I am having some trouble getting a script to work because of differences between manually typed and the "string replacement" version of the command.

The following manually typed command for example works as intended, dumping all of a log file before a date/time string in the file:
```
sed -i '1,/08\/19\/14 04/d' *.log
```

The automated string replacement version deletes the contents of the whole file:
```
sed -i '1,/$(date --date="1 day ago" +'%m')\/$(date --date="1 day ago" +'%d')\/$(date --date="1 day ago" +'%y') 04/d' *.log
```

Although echoing the command back yields the first command exactly:
```
echo "sed -i '1,/$(date --date="1 day ago" +'%m')\/$(date --date="1 day ago" +'%d')\/$(date --date="1 day ago" +'%y') 04/d' *.log"
sed -i '1,/08\/19\/14 04/d' *.log

```
Obviously echoing the command back isn't proving what it should or it would be working as intended. Please help.

As a side note.. is there any way to force a debug spit out of what  command was ACTUALLY run in a bash script? I found documents on set -x; trap read debug but it isn't doing anything particularly helpful for me in instances like this.

---

### Post by slickymaster on 2014-08-20
@getut2:
I've edited your post adding code tags to it. The use of [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by steeldriver on 2014-08-20
You're almost certainly getting tripped up by the nested quoting (in particular, the single quotes - which will prevent expansion of shell variables). Also since the expanded pattern string contains forward slashes, you should change the sed delimiter to something else such as # or |

```

$ printf 'abc 08/19/14 04 def\n' | sed "s|$(date --date="1 day ago" +'%m/%d/%y 04')|XXX|"
abc XXX def

```

(You don't need multiple date expressions)

---

### Post by getut2 on 2014-08-20
Oh jeez.. Thanks... the single date command and swapping double for single quotes got it working with the command:
```
sed -i "1,/$(date --date="1 day ago" +'%m\/%d\/%y') 04/d" *.log
```

In research I saw the delimiter replacement but it only works with s as the start from my VERY limited understanding.

I understand the syntax of my command is delete from line 1 (the 1,) to my string, leaving everything after that point. Your command uses s which is just a single line search... correct?

So in my statement, is the comma the delimiter or is the / the delimeter? Because I tried the following and it puked.
```
sed -i "1,#$(date --date="1 day ago" +'%m/%d/%y') 04#d" *.log
```

It may be because I misunderstand your example also. Am I correct that the printf is just simulating the log file so that you could test your code and output and that the sed portion of the line is the relevant part or is the printf a needed portion of the final working line?

---

### Post by steeldriver on 2014-08-20
In GNU sed, you can use alternative delimiters for commands other than the substitute (s) command - but you just need to indicate that with a backslash on the first instance e.g.

```

sed -i "1,[COLOR=#0000ff]**\|**[/COLOR]$(date --date="1 day ago" +'%m/%d/%y 04')[COLOR=#0000ff]**|**[/COLOR]d" *.log

```

> 
/regexp/[INDENT]This will select any line which matches the regular expression regexp.  If regexp itself includes any / characters, each must be escaped by a backslash (\).       The empty regular expression ‘//’ repeats the last regular expression match (the same holds if the empty regular expression is passed to the s command).  Note that modifiers to regular expressions are evaluated when the regular expression is compiled, thus it is invalid to specify them together with the empty regular expression.       
[/INDENT]
 
**\%regexp%**[INDENT]**(The % may be replaced by any other single character.)       **
[/INDENT]
 


See --> [https://www.gnu.org/software/sed/manual/sed.html#Addresses](https://www.gnu.org/software/sed/manual/sed.html#Addresses)

---

### Post by getut2 on 2014-08-20
Wow.. Thanks for taking the time to help me understand deeper than just finding the answer!

---

