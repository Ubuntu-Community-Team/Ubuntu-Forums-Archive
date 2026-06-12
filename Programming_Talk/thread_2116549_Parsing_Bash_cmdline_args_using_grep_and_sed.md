---
title: "Parsing Bash cmdline args using grep and sed"
date: 2013-02-16
forum: Programming Talk
---

### Post by RaHorakhty on 2013-02-16
I got a script that expects two args (filename and MD5hashval). I can extract just the hex output of MD5sum using md5sum test.sh | grep -om1 '^[0-9a-f]*.' For some reason, the same cmd fails when invoked from a script. Whats the best way to check cmdline arguments passed to a Bash script? Here's what the code looks like:

```
#!/bin/bash
 
while getopts "f:s:" opt; do
  case $opt in
    f)
      FILENAME=`$OPTARG | sed 's/[-a-zA-Z0-9]*=//'`
      echo ${FILENAME}
      ;;
    s)
       MD5SUM=`$OPTARG | grep -om1 '^[0-9a-f]*'` 
       echo $OPTARG
      ;;
    \?)
      echo "Invalid option: -$OPTARG" >&2
      exit 1
      ;;
    :)
      echo "Option -$opt requires an argument." >&2
      exit 1
      ;;
  esac
done
exit 0
```

the $OPTARG never gets parsed...any suggestions?

---

### Post by r-senior on 2013-02-16
I'm not quite sure where you are going with this script but when you run something like this,

```
$ md5sum temp.txt | grep -om1 '^[0-9a-f]*.'
```

you are taking the output of md5sum (on stdout) and connecting it to the input (stdin) of grep, i.e. piping.

If you put the output of md5sum into a variable, you don't put it on stdout just by naming the variable -- bash thinks you are tring to run a command like "2ff24be63bf77643012865fc8ac5909b temp.txt" so it says command not found:

```
$ MD5SUM=`md5sum temp.txt`
$ $MD5SUM
2ff24be63bf77643012865fc8ac5909b: command not found
```

You could put the content of the variable onto stdout by using echo:

```
$ echo $MD5SUM
2ff24be63bf77643012865fc8ac5909b temp.txt
```

That allows you to pipe the content of that variable to another command:

```
$ echo $MD5SUM | grep -om1 '^[0-9a-f]*'
2ff24be63bf77643012865fc8ac5909b
```

Other comments:

1. Using $() is usually easier to read than ``, e.g: 

```
MD5SUM=$(md5sum temp.txt)
```

2. Don't forget "#!/bin/bash" at the top of the script if you want to be sure bash is running the script.

3. An alternative to your grep, and perhaps slightly easier to read, is to use cut:

```
$ MD5SUM=$(md5sum temp.txt)
$ echo $MD5SUM | cut --delimiter=' ' --fields=1
2ff24be63bf77643012865fc8ac5909b

```

Having said all that, I'm not sure why you are expecting the argument to the -s option to be the raw output of md5sum. Wouldn't it make more sense to have it accept just the sum?

Maybe you could explain what you are trying to do?

---

### Post by Vaphell on 2013-02-16
if you want to see what gets inside the script
```
printf "[%s]\n" "$@"
```

example (using function instead of script)
```
$ test() { printf "[%s]\n" "$@"; }
$ test abc 'de f'
[abc]
[de f]
```

---

### Post by RaHorakhty on 2013-02-17
ok!  Thanks for the info.  Now it actually parses.  I don't really understand how grep and regular expressions work.  It so confusing! It seems like there's a million ways to parse info using reg exps. How exactly does grep work in my code? I thought it would extract just lower case hex chars 0-9a-f but it apparently truncates the string leaving all characters to the left of the first non-matching char indicated.  Anyone here sharp enough how to code it so that it returns just HEX characters (case insensitive)?  Here's the code.....

```
 #!/bin/bash

while getopts ":f:s:" opt; do
  case $opt in
    f)

      FILENAME=`echo $OPTARG | sed 's/[-a-zA-Z0-9]*=//'`
      echo ${FILENAME}
      ;;
    s)

       MD5SUM=`echo $OPTARG | grep -om1 '^[0-9a-f]*'` 
       echo ${MD5SUM}
      ;;
    \?)
      echo "Invalid option: -$OPTARG" >&2
      exit 1
      ;;
    :)
      echo "Option -$opt requires an argument." >&2
      exit 1
      ;;
  esac
done


exit 0
```

---

### Post by r-senior on 2013-02-17
To do what you describe, I think you would be better using 'tr' to remove any characters that don't match '0-9a-f':

```
$ HEX=$(echo 0123456789abcdefghijklmnopqrstuvwxyz | tr -d -c '0-9a-f')
$ echo $HEX
0123456789abcdef
```

But, if you want to process the output of md5sum, that's not what you want because the filename could have characters that match '[0-9a-f]' and they would end up in your output:

```
$ md5sum temp.txt
[COLOR="Red"]5553ae9084e054b3fb742ac623e41dc5[/COLOR]  t[COLOR="Red"]e[/COLOR]mp.txt
```

I think what you really want is the first field, delimited by one or more spaces, and 'cut' is the simplest way to do that. Your grep is extracting the first field -- you will get the longest match of '^[0-9a-z]*', which is everything up to the first space, non-inclusive -- I just think cut is simpler.

The key to understanding is that regular expressions like yours match sequences of characters, not individual characters. For filtering individual characters, something like 'tr' is your friend.

The other thing that occurs to me is that if you want to work with md5 hashes, you might just be better using Python rather than trying to process the output of md5sum using bash:

*md5.py*
```
import hashlib

def md5_hash(filename):
    with open(filename) as file:
        content = file.read()
    digester = hashlib.md5(content)
    return digester.hexdigest()

print md5_hash('temp.txt')
```

So you could just get the hex digest for a file without having to filter out any junk:

```
$ python md5.py 
cadab018255ea4f637a51655630f8bed
```

Again, it depends what you are trying to achieve ...

---

### Post by RaHorakhty on 2013-02-17
Clever!  You're as sharp as a cleaver...I'll give tr a shot.  Thanks again.

---

### Post by schragge on 2013-02-18
Just for the record, some ways to get the MD5 hash from the output of *md5sum*
```

cut -d' ' -f1 [color=blue]# that's what r-senior suggested above[/color]
awk '{print $1}'
sed 's/ .*//'
cut -c-32
egrep -o '^.{32}' [color=blue]# non-POSIX, GNU and BusyBox extension[/color]
head -c32 [color=blue]# non-POSIX, GNU and BusyBox extension[/color]
colrm 33 [color=blue]# colrm is from the package bsdmainutils[/color]
dd bs=32 count=1 2>/dev/null

``` I'm sure, you can come up with many more. The basic idea is to return either the first 32 characters or the text before the first space.

---

### Post by RaHorakhty on 2013-02-18
yea, there's more than one way to deal with strings/chars in Bash, and they're all equally confusing! I'll experiment here in my lab for a bit...keep you guys posted. thnx.

---

