---
title: "Using sed in a bash script-"
date: 2010-03-16
forum: Programming Talk
---

### Post by blur xc on 2010-03-16
I have a seemingly simple task at hand- I need to find and delete a line from a text file.  I figured out the command that does the trick, and I can make it work from the command like but it fails from inside the script.

I created a text file for testing purposes- "ls -l > test.txt"

If I enter:
```
sed -i '/file/d' test.txt
```
it works fine...
but this doesn't
```
NAME="file"
sed -i '/$NAME/d' test.txt
```

How do you use sed with a variable for the pattern to match?

Thanks,
BM

---

### Post by cubeist on 2010-03-16
I tend to use sed with pipes, this is not the only way, but it uses fairly clean code.
so first I will cat or echo a file or variable, then pipe, then the sed command you want to apply to the file or variable you have referenced.
```
echo $var_name | sed -e "s/.[0-9]*$//"
```

also, there is a difference between using single quotes and double, there is a chapter on that in this reference:
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

### Post by v8YKxgHe on 2010-03-16
```
$ NAME="foo"
$ echo '$NAME'
$NAME
```

You're using single quotes.

---

### Post by blur xc on 2010-03-16
> **cubeist said:**
> I tend to use sed with pipes, this is not the only way, but it uses fairly clean code.
so first I will cat or echo a file or variable, then pipe, then the sed command you want to apply to the file or variable you have referenced.
```
echo $var_name | sed -e "s/.[0-9]*$//"
```also, there is a difference between using single quotes and double, there is a chapter on that in this reference:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Using pipes and redirection kept giving me empty files.   I found a sed guide online, and that's how they explained using it- but in the comments after the article some posted the dangers of doing that - "cat listing.txt | sed -e '/username/d' > listing.txt", and that using the -i option was much safer.  Either way I need the pattern to match fed to the sed command by a variable, and that's not cutting it for me.

And thanks for that link- talk about information overload...

BM

---

### Post by blur xc on 2010-03-16
> **AlexC_ said:**
> ```
$ NAME="foo"
$ echo '$NAME'
$NAME
```You're using single quotes.

I just figured that out-  thanks...

```
sed -i "/$NAME/d" file.txt
```

is what I want....

BM

---

