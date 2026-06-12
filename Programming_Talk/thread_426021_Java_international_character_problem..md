---
title: "Java international character problem."
date: 2007-04-28
forum: Programming Talk
---

### Post by vedanuzal on 2007-04-28
I don't seem to be able to get international characters to display properly in jedit and when building a j2me midlet (mobile phone java app) the characters get corrupted and will not display properly on the phone.  I'm using a centrino duo laptop and kubuntu fiesty but this problem has happened on previous versions (Ubuntu as well). 

As the company i work for does work for European clients i need this fixed to use kubuntu at work and linux is a much better environment to program in.

---

### Post by steve.horsley on 2007-04-29
The first step has to be to find out what characterset the phones use - are they unicode, ISO8859-1 or something else, Then get a table of character value->glyph. Only then can you start to even know what character values you should be sending to the phone.

---

### Post by vedanuzal on 2007-04-29
Sorry maybe i wasn't clear but the problem is not with the phone's but something is wrong with the way sun java uses the ubuntu language support and it's java that is corrupting the characters.  I did find a fix that involved recompiling a library but lost it and it doesn't come up when i google it any more.

PS. And no i can't use gij or another version of java i need the real thing.

---

### Post by steve.horsley on 2007-04-30
Sorry, maybe I wasn't making myself clear. if you don't know the phone's characterset, you can't sensibly check that you are sending it the right character codes. And since java uses unicode strings, you can't know what characteset conversion to use when sending strings to the phone.

Also, how are these "special" characters being input into the program? From the editor? If so, you need to ask yourself what characterset the editor is displaying characters with, and what charcterset it is saving the .java files with, and whether javac knows the right source character set. Your problem could be that:
* the editor displays the wrong glyph on the screen - the terminal or editor or terminal font is not what you think,
* the editor is saving the source code files in a character set other than the characterset that javac thinks the file is in

To sort this out, you need to know the proper unicode values for the glyphs you wish to send to the phone (accessories->Character Map is invaluable here), and also the characterset of the phone so that java can apply the correct unicdode -> whatever conversion on output.

Pick on one character that is coming out "wrong" and find out what unicode character java thinks it is holding by casting the char to an int and printing the literal value. Then you know whether the problem is on input into your program or output from it.

---

### Post by steve.horsley on 2007-04-30
P.S. You might find these pages useful (I googled for "sms text character set):
[http://www.csoft.co.uk/sms/character_sets/gsm.htm](http://www.csoft.co.uk/sms/character_sets/gsm.htm)
[http://www.meinemullemaus.de/smstools/fileformat.html](http://www.meinemullemaus.de/smstools/fileformat.html)
[http://www.acmesystems.it/?id=72](http://www.acmesystems.it/?id=72)
So it looks like you have to specify which characterset you are using when you send the message (and then use the appropriate OutputStreamWriter codec).

---

### Post by vedanuzal on 2007-04-30
IT HAS GOT NOTHING TO DO WITH THE PHONE! The problem is that for some reason ubuntu + sun java on my laptop means that any character with an accent ie outside the English language characters is corrupted by java on my laptop.  I have read forum post about this problem before (related to Azureous mostly) but don't seem to be able to find the post with the solution.

If any one else can help me with a solution that would be good.  I think it had something to do with java using the wrong library or linking to the wrong library or something like that.

---

### Post by steve.horsley on 2007-05-01
You are refusing to look for the solution. If the phone is not displaying the characters you want it to, then either the phone is faulty (which we both agree is unlikely), of you are sending the wrong sequence of bytes to it. You need to understand all the charactersets involved and the conversions between them - how the text enters your program and gets converted from the incoming bytestream into unicode, and  how the text leaves your program, and how it gets converted from unicode to whatever characterset the phone expects.  If you refuse to investigate that, then you are beyond help.

---

### Post by vedanuzal on 2007-05-01
Mate it's you who is beyond help i know the problem is sun java because the code i'm working on is in a subversion repository and after i open a file with jedit( a java based text editor ) and save it, then the file in the repository will be corrupted if i commit and everyone at work will swear at the stupid linux guy even though it is a problem with java on ubuntu and not a linux problem.

So i suggest you actually read the post in future, and i hope your not the standard of poster on this forum cause if you are then this forum is a waist of time.

---

### Post by steve.horsley on 2007-05-01
So you say the problem is simply that jedit corrupts source files that contain special characters? That's a rather different issue, I think. Are you able to put together a small demo text file that gets corrupted by opening and editing in jedit? If so, I would be interested to see that if you can post it here.

I can think of a couple of possibilities, but again they all revolve around the question of character encoding. Do you know what character coding your source files are  using? e.g. UFT8, ISO8859-1 or Cp1252. I guess the default character coding for windows is perhaps Cp1252, but I also guess your Windows friends can't tell you for sure. That's why a sample file with several accented characters would help.

Assuming it's in Cp1252 coding, how do you tell jedit that? There is probably a way, not that it should matter - I would expect the editor to save the same as it read in most circumstances. But it may display them wrong, and some characters may get changed on output. What character coding does jedit use when it saves files? Do you know? Again, what character coding are you expecting the source file to be in? Actually, I just read that javac requires that its source code be in Latin-1 (another name for ISO8859-1) or "unicode", which is poor terminology as it doesn't distinguish between the four different possible unicode character encoding schemes that I know of.

Anyway, post a sample file with several problematic characters and a description of what those characters should be, and I'll have a look.

Actually, I can't see any significant difference between CP1252 and ISO8859-1 at the moment. Still, a sample file will tell a lot.

---

### Post by Tomosaur on 2007-05-01
Forgive me for stating the obvious - but if you're sure it's jEdit, why not just stop using it? Have you tried using a different IDE, or have you isolated the problem already to jEdit?

---

### Post by steve.horsley on 2007-05-01
Does for example, u umlaut (ü) come out as A Tilde followed by a quarter (Ã¼)?

---

### Post by gap on 2007-05-03
Steve, or anybody else who can help,

Since I have installed Feisty I am having the same problem that vedanuzal has reported. Characters with an accent come out wrong in Java programs. It appears to only affect Swing apps, like jEdit and Zend Studio. Eclipse, which uses SWT, does render the accents correctly. Please note that this has nothing to do with character encoding settings in the apps themselves. I am using the exact same versions of the program that I used without problems on Edgy and I generally know my way around character sets.

The behaviour is this: with Java 1.5, when typing an accented character, it is replaced with a totally different character (I usually get the blank square); with Java 6, accented characters are replaced with the non-accented equivalent (for example, what should be &abreve; comes out as the letter "a"). There is one exception: accented characters from the Latin-1 (ISO 8859-1) character set, such as "ü", "é" etc. are rendered correctly.

I ran the apps on sun-java5-jre and sun-java6-jre (from the Ubuntu repositories), as well as on Java 1.5 downloaded directly from Sun. There is no difference. I have used these apps with Java 1.5 on Edgy without any problems, so I guess it has to be some missing library or some sort of misconfiguration.

Here's something else that might be of help. jEdit has a keyboard troubleshooting feature. Here's a log of what happens when I try to type the characters:

*I am trying to type &abreve; (U+0103). jEdit running on Java 1.5*

> 
Event KEY_PRESSED,keyCode=0x41,keyChar=0x1e3,modifiers=0x20,consumed=0 filtered
Event KEY_TYPED,keyCode=0x0,keyChar=0x1e3,modifiers=0x20,consumed=0 passed
==> Translated to <0,1e3>
Event KEY_RELEASED,keyCode=0x41,keyChar=0x1e3,modifiers=0x20,consumed=0 passed


*Same character, jEdit running on Java 6.*

> 
Event KEY_PRESSED,keyCode=0x0,keyChar=0xffff,modifiers=0x0,consumed=0 filtered
Event KEY_PRESSED,keyCode=0x41,keyChar=0x61,modifiers=0x20,consumed=0 filtered
Event KEY_TYPED,keyCode=0x0,keyChar=0x61,modifiers=0x20,consumed=0 passed
==> Translated to <0,61>
Event KEY_RELEASED,keyCode=0x0,keyChar=0xffff,modifiers=0x20,consumed=0 passed
Event KEY_RELEASED,keyCode=0x41,keyChar=0x61,modifiers=0x0,consumed=0 passed


Any help would be greatly appreciated.

---

### Post by laxmanb on 2007-05-04
Here's a similar problem (with Netbeans):

[http://wiki.netbeans.org/wiki/view/FaqI18nLinuxAsianFonts](http://wiki.netbeans.org/wiki/view/FaqI18nLinuxAsianFonts)
[http://blogs.sun.com/katakai/entry/if_asian_fonts_are_garbled](http://blogs.sun.com/katakai/entry/if_asian_fonts_are_garbled)

and i guess you have to edit fontconfig.properties: (Google Search for more please...)
[http://www.evolutionnext.com/blog/2006/06/28/1151511032040.html](http://www.evolutionnext.com/blog/2006/06/28/1151511032040.html)

Set the font to a nice Unicode font containing the locale you want...

---

### Post by gap on 2007-05-04
laxmanb, thanks! It wasn't a font problem (accents would render correctly if they were already in the file, I just couldn't type new ones), but it was indeed a locale problem and your links were very helpful.

For reference: I had a custom value set for LC_CTYPE in /etc/environment. Once I've commented that line out the accent problem has gone away.

---

### Post by laxmanb on 2007-05-04
You're welcome!! Happy programming!

---

### Post by steve.horsley on 2007-05-04
Hmm. There are strange things going on. First, I should point out this page:
[http://java.sun.com/javase/6/docs/technotes/tools/solaris/native2ascii.html](http://java.sun.com/javase/6/docs/technotes/tools/solaris/native2ascii.html)
It says that source code should only be latin-1 (ISO8859-1) and that all other character ins the source file should be coded as unicode escaped, e.g. "\u0103".

That doesn't appear to fix the problem though. I made up a small test source file:
```
public class QuickTest {
    public static void main(String[] args) throws Exception {
        String s = "--\u0103--";
        for(int x = 0 ; x < s.length() ; x++) {
            System.out.println("value: " + (int) s.charAt(x));
        }
        System.out.println(s);
        System.out.println(System.getProperty("file.encoding"));
    }
}
```

This compiles to a classfile where that special character is stored as the byte pair C4 83. The program sees the single special charecter value 259, which is correct.
If I change the source file to hold the string "--\u00c4\u0083" then this gets stored as four bytes C3 84 C2 83 in the class file, and the program reports two characters 196 and 131. All is well. Class files store characters in UTF8 coding.

If I use my editor and put the single character a-breve in there, the editor saves the file in unicode format (refuses to save encoded as latin-1) with the byte pair C4 83 in the string. This is illegal according to the web page I linked,  and the class file contains C4 83 and the program reports one character 259. I would have expected javac to produce a class file containing  C3 84 C2 83 representing two characters, although in fact 83 is not a legal Latin-1 character. I don't think it is possible to have a legal pair of latin-1 characters that look like a pair of bytes representing one UTF8-coded character. I think saving that char as a UTF8 encoding in the source file has confused the compiler.

But then I saved a file with A double-dot (a valid character code C3 in Latin-1) and tried to compile it. The compiler gave me a warning > warning: unmappable character for encoding UTF8 and when run claimed a single character, value 65533.

I think that javac on Linux is expecting UTF8 encoded files, not Latin-1 encoded files that the documentation claims. There seems to be no way to tell javac what encoding a source file is using, according to that web page. The safe option is probably to encode all characters above \u007f in the \uxxxx format in the source file, legal Latin-1 or not, thus keeping the whole source file inside the ASCII character set.

Another odd thing is that I tried one editor (bluej) here, and it incorrectly displays the character \u0103 while editing the source file. But since you shouldn't be embedding these characters directly in the source code that's not really an issue. The confusion between Latin-1 and UTF8 encoded source files is an issue though.

UPDATE:
I then found that javac can accept a -encoding option so you can say:
javac -encoding ISO8859-1 QuickTest.java
or 
javac -encoding UTF8 QuickTest.java
And I believe that the default platform encoding on Linux (which is used if -encoding is not specified) is UTF8.
Here's the link: [http://java.sun.com/javase/6/docs/technotes/tools/solaris/javac.html](http://java.sun.com/javase/6/docs/technotes/tools/solaris/javac.html)

So this just brings us down to the ability of various editors to display characters correctly and to be able to know/control the character coding that they read/save files in.

---

### Post by gap on 2007-05-04
I don't program in Java myself, and having accented characters in PHP source code is not generally a problem. This was really an issue of keyboard input filtering in Java apps. By following one of the links offered by laxmanb I came to the [Supported Locales]("http://java.sun.com/javase/6/docs/technotes/guides/intl/locale.doc.html#jfc") page on Sun's website. The table on that page all but describes the issue:

> Central European locale: Linux encodings unsupported, Peered AWT components supported.

If someone else has this problem, they should try:

```
env -u LC_CTYPE jedit  # or whatever the program happens to be
```

---

### Post by vedanuzal on 2007-05-11
PS I did solve the problem and it was simple once i got it working and a gui for this would be nice.

I changed the encoding back to iso-8859-1 and once i rebooted jedit and the wireless toolkit seemed to handle accents properly.

Java + Linux plus utf8 seems to cause problems.  not sure how java works on the new debian release as that uses utf8 now too.

---

