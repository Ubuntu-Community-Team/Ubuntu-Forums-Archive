---
title: "hexdump string format (and right-click gnome-terminal arguments)"
date: 2009-10-17
forum: Programming Talk
---

### Post by sdaau on 2009-10-17
Hi all,

I wanted a script, which could either accept a filename as a bash argument, or a filename from a right-click selection (if the script is used in ~/.gnome2/nautilus-scripts ), and then raise a terminal window, and show a hex dump of that file. 

I had plently of trouble passing the right argument to gnome terminal, especially since a string is composed which is finally called - the trick is, of course, to store the "gnome-terminal" and its argument in two separate string variables; and at call time - call using both strings, having quoted the argument string there. Since I found that so troublesome, thought I'd document the code for the script, which is included below. 

However, now the problem comes for me, in that I cannot get hexdump to show data the way I want it. In its canonical format output, hexdump shows both hex and ASCII representation:
```

$ hexdump -C /etc/issue 
00000000  55 62 75 6e 74 75 20 39  2e 30 34 20 5c 6e 20 5c  |Ubuntu 9.04 \n \|
00000010  6c 0a 0a                                          |l..|
00000013

```Also, there is a possibility to use format specifiers for hexdump:
```

$ hexdump -e '"%06.6_ax " 8/1 "%_c " "\n"' /etc/issue 
000000 U b u n t u   9
000008 . 0 4   \ n   \
000010 l \n \n     
$ hexdump -e '"%06.6_ax " 8/1 "%01x " "\n"' /etc/issue 
000000 55 62 75 6e 74 75 20 39
000008 2e 30 34 20 5c 6e 20 5c
000010 6c a a          

```However, I'd prefer an output which looks like:
```

00000000  55 (U) , 62 (b) , 75 (u)  [... snip ...]
00000010  6c (l) , 0a (.) , 0a (.)

```But, if I try to do something like that in a format specifier string option for hexdump, I get:
```

$ hexdump -e '"%06.6_ax " 8/1 "%01x %_c " "\n"' /etc/issue 
hexdump: byte count with multiple conversion characters

```And the manpage for hexdump does state:
[quote=http://www.manpagez.com/man/1/hexdump/]
It is an error to specify a byte count as well as multiple conversion
     characters or strings unless all but one of the conversion characters or
     strings is _a or _A.
[/quote]
which I'm not sure how to understand - if you don't specify a byte count, and you specify multiple conversion characters, they are applied to *consecutive* bytes (as per default block organization in hexdump) - and so the _c gets to display the "first" character of that "string" block only:
```

$ hexdump -e '"%06.6_ax " "%01x %_c " "\n"' /etc/issue 
000000 6e756255 t 
000005 2e392075 0 
00000a 6e5c2034   
00000f a0a6c5c  

```So, is there any possibility for me to make hexdump produce the kind of output I prefer (hex value, then ASCII representation of each individual byte consecutively)?

Thanks,
Cheers !

PS. The code for "viewHexdump" script - toss in ~/.gnome2/nautilus-scripts to have right-click on a file access via Scripts context menu entry: 
```

# what works directly in gnome-terminal/bash: 
# hexdump -e '" " 1/1 "%02x" " "' /etc/issue | less
# gnome-terminal -e "bash -c \"echo aa | less\"" -t "hexdump"
# gnome-terminal -e "bash -c \"hexdump -e '\\\" \\\" 1/1 \\\"%02x\\\" \\\" \\\"' /etc/issue | less\"" -t "hexdump"
# use 'echo' instead of 'gnome-terminal -e' to debug the argument passed to gnome-terminal; will see:
# bash -c "hexdump -e '\" \" 1/1 \"%02x\" \" \"' /etc/issue | less" -t hexdump

# though note: the following command:
# tzt="gnome-terminal -e \"bash -c \\\"hexdump -e '\\\\\\\" \\\\\\\" 1/1 \\\\\\\"%02x\\\\\\\" \\\\\\\" \\\\\\\"' /etc/issue | less \\\"\"" ; echo $tzt; $tzt
# will fail with "Failed to parse arguments: Argument to "--command/-e" is not a valid command: Text ended before matching quote was found for ". (The text was '"bash')"
# however, the string it generates works - if you just copy/paste it in gnome-terminal !!

# https://bugs.launchpad.net/terminator/+bug/247330
# gnome-terminal uses g_shell_parse_argv() on the argument, which "does a semi-arbitrary weird subset of the way the shell parses a command line."
# xterm attempts to execv() and failing that calls the shell using execlp.
# AND - from gnome-terminal --help-all:
#   -e, --command                   Execute THE ARGUMENT to this option inside the terminal

# but note how the parsing /concat goes in this statement:
#       {  }{ }{   }{ }{   }
# $ tzt='\"'"'"' a '"'"' \"' ; echo $tzt
# out> \"' a ' \"
# maybe the only way to get both escaped " and ' in a string? 
# nope, still the same argument problem for
# $ tzt='gnome-terminal -e "bash -c \"hexdump -e '"'"'\\\" \\\" 1/1 \\\"%02x\\\" \\\" \\\"'"'"' /etc/issue | less\""' ; echo $tzt; $tzt

# however, since this is argument problem, can just use different quoting w/ two strings, 
# where the other string is the arg to gnome-terminal - and quote it in the calling part!
# $ tzt='gnome-terminal -e ';tzb='bash' ; echo $tzt "\"$tzb\""; $tzt "\"$tzb\""
# note, stracing that, gives
# execve("/usr/bin/gnome-terminal", ["gnome-terminal", "-e", "\"bash -c \\\"tail -f /etc/issue\\\"\""...], [/* 38 vars */]) = 0
# and finally, THIS works:
# $ tzt='gnome-terminal -e ';tzb='bash -c "tail -f /etc/issue"' ; echo $tzt "$tzb"; $tzt "$tzb"
# $ tzt='gnome-terminal -e ';tzb='bash -c "tail -f /etc/issue"' ; echo $tzt "$tzb"; strace -o sout.txt $tzt "$tzb"


TFILE=$(readlink -f $1)
if [ ! -e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ] ; then
TFILE=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
fi

# set GNT and GNTARG string variables

GNT='gnome-terminal -e '

# GNTARG could be done differently - 
# - but lets suffer more by concat-ing \' and \" encapsulated strings

##      {              }{      }{ } 
#GNTARG='bash -c "less '"$TFILE"'"'

##      {        [           }{ }{                        }{ }{ }{      }{       ]}
#GNTARG='bash -c "hexdump -e '"'"'\" \" 1/1 \"%02x\" \" \"'"'"' '"$TFILE"' | less"'

# alas, this fails with hexdump: byte count with multiple conversion characters
##      {        [           }{ }{                             }{ }{ }{      }{       ]}
#GNTARG='bash -c "hexdump -e '"'"'\" \" 1/1 \"%02x-%_c \" \" \"'"'"' '"$TFILE"' | less"'
# probably with hexdump it is impossible to show the same byte as  
#   both hex and char close together in a format specifier string

# however, od gives a slightly closer output to that
#   - although not as customizible as hexdump
##      {                        }{      }{        } 
#GNTARG='bash -c "od -w8 -t acxC '"$TFILE"' | less"'

# still, probably hexdump canonical output is closest to have hex+ASCII close together
#      {                    }{      }{        } 
GNTARG='bash -c "hexdump -C '"$TFILE"' | less"'


# set the gnome-terminal window title in this step

# debug check echo 
echo $GNT "$GNTARG" -t "hexdump $TFILE"

# and run
$GNT "$GNTARG" -t "hexdump $TFILE"

# ... im in ur shell, passing ur argumentz ...

```.





EDIT: Well, I got sort of an answer via [#488473 - bsdmainutils: 'hexdump -e' needs command line examples. - Debian Bug report logs]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=488473") - from the "a table of byte#, hex, decimal, octal, ASCII" example there, it seems one needs to pass -e argument multiple times, for each format of the "current" byte desired, so close to what I want is:
```

$ hexdump -e '1/1 "(0x%01X "' -e '1/1 "%c) "", "' /etc/issue
(0x55 U) , (0x62 b) , (0x75 u) , (0x6E n) , (0x74 t) , (0x75 u) , (0x20  ) , (0x39 9) , (0x2E .) , (0x30 0) , (0x34 4) , (0x20  ) , (0x5C \) , (0x6E n) , (0x20  ) , (0x5C \) , (0x6C l) , (0xA 
) , *

```except now I cannot figure out how to group, say only five entries per row - and how to add the address for such a group :)


EDIT2: I think I finally understand better why what I want, cannot be done with hexdump - consider the following snippet (replace the comments with ;\ to test it): 
```

HEXP1='1/ " " "%02_ax" " |  "'    # for each iteration, output space, adress, and pipe ;
HEXP2='/1 " 0x%02X "'         # for each byte count, output hex format ;
HEXP3='/1 " "'             # for each byte count, output space ;
HEXP4='/1 " %c, "'        # for each byte count, output char format ;
HEXP5='6/1 " " "\n"'        # for each 6 iterations of a bytes each, output space - and output \n at end when done (here can change for number of columns shown) ;

hexdump -e "$HEXP1" -e "$HEXP2" -e "$HEXP3" -e "$HEXP4" -e "$HEXP5" /etc/issue 

 00 |   0x55  0x62  0x75  0x6E  0x74  0x75      U,  b,  u,  n,  t,  u,     
 06 |   0x20  0x39  0x2E  0x30  0x34  0x20       ,  9,  .,  0,  4,   ,     
 0c |   0x5C  0x6E  0x20  0x5C  0x6C  0x0A      \,  n,   ,  \,  l,  
,     
 12 |   0x0A  0x    0x    0x    0x    0x        
,  ,  ,  ,  ,  ,     

# BUT !! if in a single -e, the same HEXPs are interpreted as for consecutive bytes !!!

hexdump -e "$HEXP1 $HEXP2 $HEXP3 $HEXP4 $HEXP5" /etc/issue 

 00 |   0x55   b,      
 09 |   0x30   4,      
 12 |   0x0A   ,      


```which makes it easier to see that hexdump, at each iteration composes the byte string for each string format separately - and then in the end, concatenates them to form a row. Thus, for characters 1,2,3, I'd get string format a as a = a1 . a2 . a3 ... and string format b as b = b1 . b2 . b3 ... and the row would be a.b = a1 . a2 . a3 ... b1 . b2 . b3 - which means there would be no chances of getting the output mixed as in a1 . b1 . a2 . b2 . ... an . bn . Which is a shame :)


EDIT3: Well, finally got it the way I want - but have to iterate byte by byte from bash, obtain a string description via hexdump, and concatenate accordingly. Which means - it is slow... but it shows what I want to see :) 
```

# filename: hdtest
FNAME=$(readlink -f $1)
FSIZEA=$(stat -c%s "$FNAME")
FSIZE=$((FSIZEA - 1))
NUMCOLS=5
HEXP1='1/ " " "%02_ax" " |  "'    # for each iteration, output space, adress, and pipe ;
HEXP2='1/ " (0x%02X"'         # for each iteration, output hex format ;
HEXP3='/1 " (0x%02X, "'         # for each byte count, output hex format ;
HEXP4='/1 " %c) "'        # for each byte count, output char format ;

#  hexdump -s 0 -n 1 -e '/1 " (0x%02X, "' -e '/1 " %c) "'  /etc/issue

TOUT=""
CCNT=1 # so we start from zero

# for i in $(seq 0 1 $FSIZE )
# not sure why have to decrement twice

for i in $(seq 0 1 $(($FSIZE - 1)) ) 
do
	CCNT=$(($CCNT - 1))
	if [ "$CCNT" -eq 0 ] ; then 
		CCNT=$NUMCOLS
		TOUT="$TOUT""
"
		TOUT="$TOUT""`hexdump -s "$i" -n "1" -e "$HEXP1" -e "$HEXP3" -e "$HEXP4" $FNAME`"
	else
		TOUT="$TOUT""`hexdump -s "$i" -n "1" -e "$HEXP3" -e "$HEXP4" $FNAME`"
	fi
done
echo "$TOUT" # multiline

```

Then, can test it with: 
```

$ hexdump -e '/1 " (0x%02X, "' -e '/1 " %c) "'  /etc/issue
 (0x55,  U)  (0x62,  b)  (0x75,  u)  (0x6E,  n)  (0x74,  t)  (0x75,  u)  (0x20,   )  (0x39,  9)  (0x2E,  .)  (0x30,  0)  (0x34,  4)  (0x20,   )  (0x5C,  \)  (0x6E,  n)  (0x20,   )  (0x5C,  \)  (0x6C,  l)  (0x0A,  
) *

$ ./hdtest /etc/issue | less

 00 |   (0x55,  U)  (0x62,  b)  (0x75,  u)  (0x6E,  n)  (0x74,  t) 
 05 |   (0x75,  u)  (0x20,   )  (0x39,  9)  (0x2E,  .)  (0x30,  0) 
 0a |   (0x34,  4)  (0x20,   )  (0x5C,  \)  (0x6E,  n)  (0x20,   ) 
 0f |   (0x5C,  \)  (0x6C,  l)  (0x0A,  
) 

```

---

### Post by sdaau on 2010-08-06
Oh, well - I should have found this page earlier - it explains it all:

[hexdump format strings : technovelty](http://www.technovelty.org/linux/tips/hexdump.html)

for command line usage, simply single quotes are needed - so hexdump gets the double quotes; also if you need to display bytes "twice" (say once as byte, another as character) you'd need two separate -e statements - consider:
```

# this example is with single -e statement, and is incorrect:

$ echo abcdefghijklmnopqrs | hexdump -v -e '"%07.1_ax \t"' -e '4/1 "0x%02x, " "   " 4/1 "0x%02x, " "\t" 8/1 " %_c"' -e '"\n"'
      0 	0x61, 0x62, 0x63, 0x64,   0x65, 0x66, 0x67, 0x68,	 i j k l m n o p
     10 	0x71, 0x72, 0x73, 0x0a,   0x  , 0x  , 0x  , 0x  ,	        


# this example is correct:

$ echo abcdefghijklmnopqrs | hexdump -v -e '"%07.1_ax \t"' -e '4/1 "0x%02x, " "   " 4/1 "0x%02x, " "\t"' -e '8/1 " %_c"' -e '"\n"'
      0 	0x61, 0x62, 0x63, 0x64,   0x65, 0x66, 0x67, 0x68,	 a b c d e f g h
      8 	0x69, 0x6a, 0x6b, 0x6c,   0x6d, 0x6e, 0x6f, 0x70,	 i j k l m n o p
     10 	0x71, 0x72, 0x73, 0x0a,   0x  , 0x  , 0x  , 0x  ,	 q r s \n    


```

Cheers!

---

