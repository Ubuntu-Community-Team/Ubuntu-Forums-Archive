---
title: "Python encoding problem"
date: 2008-02-09
forum: Programming Talk
---

### Post by IdanH14 on 2008-02-09
i started to learn python recently.
my goal is to make a program which will grab dictionaries' web-pages. The problem is, i'm a hebrew speaker, and python seems not to recognize hebrew characters.
Here's the function I wrote:
```
def extract(word):
    sock = urllib.urlopen("http://www.babylon.com/definition/" + str(word).lower() + "/he") # sets and opens the dictionary page
    parser = SGMLDictionaryReader() # as expected, SGMLDictionaryReader is a decedent of SGMLParser
    parser.feed(sock.read()) # feeds parser with the url data
    sock.close()
    parser.close()
    print parser.text
```

```
**output:**
the following list:
['&', '=275', 'churn', 'Babylon', 'churn', "(\xd7\xa4')", '(\xd7\xa9"\xd7\xa2)', 'Churn', 'vessel', 'stir', 'move', '\xd7\xaa\xd7\xa8\xd7\x92\xd7\x9d:', '\xd7\x90\xd7\xa0\xd7\x92\xd7\x9c\xd7\x99\xd7\xaa', '\xd7\xa7\xd7\xa8\xd7\x95\xd7\x90\xd7\x98\xd7\x99\xd7\xaa', '\xd7\x94\xd7\x95\xd7\x9c\xd7\xa0\xd7\x93\xd7\x99\xd7\xaa', '\xd7\xa6\xd7\xa8\xd7\xa4\xd7\xaa\xd7\x99\xd7\xaa', '\xd7\x92\xd7\xa8\xd7\x9e\xd7\xa0\xd7\x99\xd7\xaa', '\xd7\xa2\xd7\x91\xd7\xa8\xd7\x99\xd7\xaa', '\xd7\x90\xd7\x99\xd7\x98\xd7\x9c\xd7\xa7\xd7\x99\xd7\xaa', '\xd7\x99\xd7\xa4\xd7\xa0\xd7\x99\xd7\xaa', '\xd7\xa7\xd7\x95\xd7\xa8\xd7\x99\xd7\x90\xd7\xa0\xd7\x99\xd7\xaa', '\xd7\xa4\xd7\x95\xd7\xa8\xd7\x98\xd7\x95\xd7\x92\xd7\x96\xd7\x99\xd7\xaa', '\xd7\xa8\xd7\x95\xd7\xa1\xd7\x99\xd7\xaa', '\xd7\xa1\xd7\xa8\xd7\x91\xd7\x99\xd7\xaa', '\xd7\xa1\xd7\xa4\xd7\xa8\xd7\x93\xd7\x99\xd7\xaa', '\xd7\xa9\xd7\x95\xd7\x95\xd7\x93\xd7\x99\xd7\xaa', '\xd7\x98\xd7\x95\xd7\xa8\xd7\xa7\xd7\x99\xd7\xaa', '\xd7\xa0\xd7\x95\xd7\xa1\xd7\xa4\xd7\x95\xd7\xaa', 'inquietude', 'whisk']

```

the weird character segments are supposed to be hebrew character.
I tried to convert those characters to hebrew using:
```
encode('iso-8859-8', 'ignore')
```
where it fits. however. it was unsuccessful. the error message was:
```
UnicodeDecodeError: 'ascii' codec can't decode byte 0xd7 in position 1: ordinal not in range(128)
```
needless to say, i'm on ubuntu gutsy.

any help, in any form would be appreciated. Thank you all!

---

### Post by ghostdog74 on 2008-02-09
you can give it a shot..
```

    text.decode("iso-8859-8")
    text.decode("cp1255")
    text.decode("cp862") 

```

---

### Post by IdanH14 on 2008-02-09
> **ghostdog74 said:**
> you can give it a shot..
```

    text.decode("iso-8859-8")
    text.decode("cp1255")
    text.decode("cp862") 

```

I've tried this command:
```
print parser.text[0].decode("iso-8859-8", "ignore")
# text[0] was chosen just because it looked good
```
And got this error message:
```
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-4: ordinal not in range(128)
```
I got the same error in every option you gave me.
Thanks for your help!

---

### Post by pmasiar on 2008-02-09
[http://www.python.org.il/](http://www.python.org.il/) is supposed to have links for you, but I cannot tell: it is in hebrew :-)

see also [http://docs.python.org/lib/standard-encodings.html](http://docs.python.org/lib/standard-encodings.html)

---

### Post by IdanH14 on 2008-02-09
> **pmasiar said:**
> [http://www.python.org.il/](http://www.python.org.il/) is supposed to have links for you, but I cannot tell: it is in hebrew :-)

see also [http://docs.python.org/lib/standard-encodings.html](http://docs.python.org/lib/standard-encodings.html)

python.org.il is down due to server replacement. :(
I'll just wait to its return.
I already saw the standard-encoding page. I found it on google. The problem is it doesn't help. :(
Thanks anyway!

---

### Post by wdk on 2008-02-09
I'm going to go out on a limb and suggest that you may not have to do any encoding or decoding at all.

If I copy your output list into a variable (test) and do
```

print test

```
it prints your list with all the backslashed characters, just as you posted it.

However, if I then try
```

print test[12]

```
I get what appear to be Hebrew characters (I don't actually read Hebrew, though)

The babylon dictionary website actually appears to use utf-8 encoding, as does ubuntu, which means you shouldn't technically have to mess with it too much.

It may be useful to try printing the text you get back from sock.read()
When I tried this I got actual Hebrew chars within the HTML, so it appears print is smart enough to figure out you are in fact using utf-8 when you feed it a string. (If you feed it something else, it may not, which may be why you are getting the backslashed chars when you print your list)

Hope this helps!

---

### Post by IdanH14 on 2008-02-10
Incredibly as it may sound, the problem had nothing to do with encoding. My IDE, Eclipse with Pydev was the problem. :(
I tried the same script on Geany and it worked like a charm. :(
Now I have a different problem. It seems that python can't recognize some of the characters it prints, and therefore it print them as &#65533;.
How can I recognize and remove these &#65533; from the print or even recognize the foul characters in the string and remove them from there?
Thank you all! You were much helpful!

EDIT: Irrelevant question. I did it with this function:
```
def makeAscii(str):
    s = ""
    for i in str:
        try:
            i.encode("iso-8859-8")
        except UnicodeEncodeError:
            continue
        else:
            s += i
    return s
```
Thanks you all!

---

### Post by IdanH14 on 2008-02-10
Since  I don't want to open a new thread:
I have a glade interface combined with a class I wrote. The class has a function which connects to the dictionary web site and grabs the translation, and return in the proper format, which is a string. I then take the returned string, make a TextBuffer out of it, and set this TextBuffer as my Gtk.TextView buffer. The process occurs once the user presses a certain Gtk.Button. The only problem is that the function uses the function liburl.read(), and this function makes the entire interface get stuck the for a short while while it receives the information from the web site. I thought about using a thread, but I have no idea how to make the thread effect the TextView widget, if that is necessary. What should I do?
Thank you all!

---

### Post by IdanH14 on 2008-02-11
Bump! :)

---

