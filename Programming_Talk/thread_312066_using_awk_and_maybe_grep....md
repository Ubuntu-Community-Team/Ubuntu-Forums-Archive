---
title: "using awk and maybe grep..."
date: 2006-12-03
forum: Programming Talk
---

### Post by ilovenicotine on 2006-12-03
I'm simply trying to write a couple scripts to automate a few of the things I end up doing every time I re-install ubuntu.

One of which is editting these three files:
/etc/X11/gdm/Xsession
/etc/X11/gdm/Init/Default
/etc/X11/gdm/PostLogin/Default

I want to add a few lines to the bottom of the files but above the "exit 0" at the end.  I've figured out that tee isn't powerful enough but awk is insanely complex for someone at my level.

After searching for a while I'm about to give it a rest for a while, but this is really something I'd like to learn more about as I think it will come in handy again down the road.

Anyone know of a "beginner" link that might be able to help me learn about awk and the use of grep with it?
Or a quick and simple answer to my challenge to get me started?

---

### Post by ghostdog74 on 2006-12-03
[http://www.unix.org.ua/orelly/unix/sedawk/index.htm]("http://www.unix.org.ua/orelly/unix/sedawk/index.htm")

---

### Post by mssever on 2006-12-03
> **ghostdog74 said:**
> [http://www.unix.org.ua/orelly/unix/sedawk/index.htm](http://www.unix.org.ua/orelly/unix/sedawk/index.htm)

Well, that link's dead. I would use the man page (man awk), but I don't know if it's beginner-oriented enough for you.

---

### Post by ilovenicotine on 2006-12-03
I figured out a pretty ghetto way of doing this with sed piped to tee.  It works pretty good but for some reason if it can't find the string I'm looking for, it overwrites the contents with a blank line.

In my case this is fine because I know that the files I'm editing  contain "exit 0" and I can add it back when I'm done (preventing future scripts from erasing the file contents)...

So I delete "exit 0":
sed -e "/exit\ 0/d" "test.cfg" | tee  test.cfg (note: there are two spaces between tee and test.cfg not shown here, see 2. below)

append the file with my code:
echo "rad" | tee -a test.cfg
echo "super rad" | tee -a test.cfg

then append "exit 0" in again:
echo "exit 0" | tee -a test.cfg

There are, like I implied, a couple of caveats:
1. if "exit 0" doesn't exist it erases the file having not written a thing...wtf?
2. for some reason | tee test.cfg also erases the file. **I got this working by using two spaces in between "tee" and "test.cfg".** (very finicky, see 3.)
3. sometimes sed -e "/exit\ 0/d" "test.cfg" | tee  test.cfg (with two spaces in there) plain erases my file out of nowhere... following echo's are appended to an the empty file.

can anyone thinks of the "legit" way of doing this?

---

### Post by ilovenicotine on 2006-12-03
this works much better and at this point is fully good enough:

sed "/exit\ 0/d" "test.cfg" > test2.cfg
mv test2.cfg test.cfg
echo "rad" >> test.cfg
echo "super rad" >> test.cfg
echo "exit 0" >> test.cfg

seems that piping things messes up the order in which things are processed.  too big for me to wrap my head around right now but good enough reason for me...
thanks tom.

---

### Post by mssever on 2006-12-03
> **ilovenicotine said:**
> I figured out a pretty ghetto way of doing this with sed piped to tee.  It works pretty good but for some reason if it can't find the string I'm looking for, it overwrites the contents with a blank line.

In my case this is fine because I know that the files I'm editing  contain "exit 0" and I can add it back when I'm done (preventing future scripts from erasing the file contents)...

So I delete "exit 0":
sed -e "/exit\ 0/d" "test.cfg" | tee  test.cfg (note: there are two spaces between tee and test.cfg not shown here, see 2. below)

append the file with my code:
echo "rad" | tee -a test.cfg
echo "super rad" | tee -a test.cfg

then append "exit 0" in again:
echo "exit 0" | tee -a test.cfg

There are, like I implied, a couple of caveats:
1. if "exit 0" doesn't exist it erases the file having not written a thing...wtf?
2. for some reason | tee test.cfg also erases the file. **I got this working by using two spaces in between "tee" and "test.cfg".** (very finicky, see 3.)I'm not sure what's happening there...bash doesn't care about the number of spaces.
> 3. sometimes sed -e "/exit\ 0/d" "test.cfg" | tee  test.cfg (with two spaces in there) plain erases my file out of nowhere... following echo's are appended to an the empty file.

can anyone thinks of the "legit" way of doing this?

OK...Here's something I threw together just now: ```

filename="foo"
tmpFile="/tmp/$filename"
IFS="\n"
numLines=$(wc -l "$filename" | awk '{print $1}')
i=0
cat "$filename" | while [ $i -lt $numLines ]; do
    read Line
    if echo "$Line" | grep 'exit 0' > /dev/null; then
        Line="Foo\nFoo2\n$Line"
    fi
    echo -e "$Line" >> "$tmpFile"
    let i=$i+1
done
cp "$tmpFile" "$filename"
```This still won't handle files that don't end in exit 0, but it won't clobber them, either. There's got to be a way to write a regular expression that matches EOF...

EDIT: I guess you found a solutino while I was typing...

---

### Post by ghostdog74 on 2006-12-03
> **mssever said:**
> Well, that link's dead. I would use the man page (man awk), but I don't know if it's beginner-oriented enough for you.

No.its not dead.

---

### Post by mssever on 2006-12-04
> **ghostdog74 said:**
> No.its not dead.

This is what I see at that page: > page deleted Hmm... :-k

---

