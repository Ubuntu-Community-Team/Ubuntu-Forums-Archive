---
title: "GTK load rich text"
date: 2010-07-02
forum: Programming Talk
---

### Post by kumoshk on 2010-07-02
I know how to create a text editing widget that will allow you to type out rich text. However, I need to figure out how to load a potentially large file with tags (such as <i></i> for italics) and have the tagged text be rich. This needs to be done in a TextView (not an HTML widget or a SourceView).

Here are some links that show how to add it as you type (rather than how to load it), using texttags, texttagtables and buttons, in a TextView and TextBuffer:
&#8226; [http://www.kksou.com/php-gtk2/articles/apply-styles-to-GtkTextView-using-GtkTextTag---Part-1.php](http://www.kksou.com/php-gtk2/articles/apply-styles-to-GtkTextView-using-GtkTextTag---Part-1.php)
&#8226; [http://www.kksou.com/php-gtk2/articles/apply-styles-to-GtkTextView-using-GtkTextTag---Part-2---toggle-the-formatting-on-and-off.php](http://www.kksou.com/php-gtk2/articles/apply-styles-to-GtkTextView-using-GtkTextTag---Part-2---toggle-the-formatting-on-and-off.php)
&#8226; [http://www.learnpygtk.org/pygtktutorial/textviewexamples.html](http://www.learnpygtk.org/pygtktutorial/textviewexamples.html)

---

### Post by pbrane on 2010-07-02
Not to be obvious but you need to parse the RTF file and apply the GtkTextTags as you encounter RTF tags. Create a texttag for each different type of RTF format tag. In the GtkTextView buffer the text itself is not RTF. When you want to save the file that's when you parse the GtkTextTags and write out the RTF format tags to a file on disc.

---

### Post by kumoshk on 2010-07-03
> **pbrane said:**
> Not to be obvious but you need to parse the RTF file and apply the GtkTextTags as you encounter RTF tags. Create a texttag for each different type of RTF format tag. In the GtkTextView buffer the text itself is not RTF. When you want to save the file that's when you parse the GtkTextTags and write out the RTF format tags to a file on disc.

Okay. I think I got it figured out. So, basically I just need to use some string function to get the starting and ending values of the markup I'm using, and do something like this with it with start and end being the values I just mentioned:
```
textbuffer.apply_tag(self.texttag_italic, start, end)
```

---

### Post by kumoshk on 2010-07-03
> **kumoshk said:**
> So, basically I just need to use some string function to get the starting and ending values &#8230;
So, anyone know if there's something like a find function in Glib, or anything else available in Vala?

I mean, a function like this:
int find(myString, searchVal) //returns the starting int representing the starting position of searchVal. -1 if it's not there.

It doesn't seem to exist in the Glib string class, anyhow. That's kind of odd. Python and Lua seem to have such.

---

### Post by pbrane on 2010-07-03
Glib::ustring has *find* and *substr* functions. Maybe there are some equivalent functions usable in PyGtk or Vala. I usually work in C/C++ so I'm not sure. A quick search doesn't find anything. Although I have never used it you may take a look at GScanner, GLib's lexical scanner.

You may end up writing your own *find()*.

---

### Post by kumoshk on 2010-07-04
> **pbrane said:**
> Glib::ustring has *find* and *substr* functions. Maybe there are some equivalent functions usable in PyGtk or Vala. I usually work in C/C++ so I'm not sure. A quick search doesn't find anything. Although I have never used it you may take a look at GScanner, GLib's lexical scanner.

You may end up writing your own *find()*.

Hmm. That might be something to bring up to the Vala list. Vala has GLib&#8212;I wonder why the find method isn't in its string class. It has the method for substrings. Maybe it was an oversight. It's hard to imagine that it was anything else, seeing as they have the replace method, which should require the same information&#8212;unless there is another (preferred) way of doing this for some reason. I don't know. I'll have to dig up that list and ask.

---

### Post by kumoshk on 2010-07-06
I think I've found a solution. It doesn't involve the string class, but fortunately, we're working with a TextBuffer instead, with which we can use TextIter objects. I can place one of those in my loaded TextBuffer and then call the TextIter.forward_search() method (instead of the find method on a string), with the proper parameters. It looks like what I want, but I haven't tried it yet. Here's a link about the method:

[http://www.valadoc.org/gtk+-2.0/Gtk.TextIter.forward_search.html](http://www.valadoc.org/gtk+-2.0/Gtk.TextIter.forward_search.html)

backward_search should work, too, but I might as well start from the beginning.

---

### Post by smartboyathome on 2010-07-16
I found this on Google, and I just wanted to post to let you know I am in the same boat as you except on PyGTK. I already had a working parser for the older, third party InteractivePangoShell script, so I'm going to see if I can do anything with that. If I actually get results I'll let you know, perhaps we can help each other out.

By the way, I would look at the foreach method of the gtk.TextTagTable (see [here](http://www.pygtk.org/docs/pygtk/class-gtktexttagtable.html), should also be available for Vala) instead of using forward_search and backward_search. The latter two don't actually do what either of us want, they just search for a string, which a gtk.TextTag is not.

---

### Post by kumoshk on 2010-07-16
Cool. Glad to know I'm not the only one. I'll let you know what I figure out.

Actually, though, I *believe* a string is exactly what I want. I'm not searching for texttags. I'm searching for my own personal markup in string form (something like <i>italicized text</i>), and then replacing the markup with texttags. I'm not loading in rtf or HTML files, though—just my own plain txt files with occasional markup here and there, for simple formatting. (The markup won't be the same for every file—so it needs to be customizable.) I mean, the idea is to get formatted text out of plain text files—for instance, in the following file,
[http://www.gutenberg.org/cache/epub/13835/pg13835.txt](http://www.gutenberg.org/cache/epub/13835/pg13835.txt)
You might notice that the italicized text is all surrounded in underscores. This is the sort of file I want to load in, and in my e-book reader make the text italicized.

Is it the same sort of thing that you're working on, or is it kind of different?

I haven't tried out the solution I proposed in that other post, yet, due to other obligations, but eventually …

---

### Post by smartboyathome on 2010-07-16
Ah, I'm trying to do the exact opposite right now. I want to take the text tags markup and *save* it into a file, rather than just loading it from a file (I'll get to that after I know how to save it). I've stumbled across one parser for tags, but unfortunately i didn't bookmark it (should have). Seems like applying tags should be easier than saving them since, for your problem, you basically want to get the position of the underscore, delete it, and replace it with a text tag (either start or end). I can tell you that you are going to need regular expressions, but having experience with them in my last parser, I haven't found a way to match common symbols (for example, matching two underscores in something _like this_). If anything, the best suggestion I would have is to find the position of the first underscore, then walk to the second using some type of recursive function and utilizing gtk.TextBuffer.get_iter_at_offset() and gtk.TextIter.get_offset().

---

### Post by kumoshk on 2010-07-16
> **smartboyathome said:**
> &#8230; then walk to the second using some type of recursive function and utilizing gtk.TextBuffer.get_iter_at_offset() and gtk.TextIter.get_offset().

Something I like to try a lot in text parsing is the split function of a string (that exists in Python, too). It's pretty nice: i.e.
```
markedUpList=myFileString.split("_")
i=0
for x in markedUpList:
    if i%2!=0 and i!=0:
        #Get the position of the end of your buffer
        myBuffer.text+=x #add the text to the buffer of your TextView
        #Get the position of the end of your buffer again
        #apply the texttag using those two coordinates
    else:
        myBuffer.text+=x
    i+=1
```

But then, if the file ever uses an underscore for something besides italics (such as with an email address), I'd be in trouble with this, unless I took care of such first. That shouldn't be terribly common with novels, but it happens sometimes (especially in newer ones). I'm not sure how efficient this method would be, though. An algorithm to take care of that shouldn't be too hard, though. Basically, I just need to determine if the characters around each underscore are whitespace, punctuation (or other such symbol) or part of a word, as well as whether it's repeating, and act accordingly (i.e. replace the markup ones with another symbol and leave the other ones be).

---

### Post by kumoshk on 2010-07-16
> **kumoshk said:**
> Something I like to try a lot in text parsing is the split function of a string &#8230;
Hmm. Now that I look at this, it seems I wouldn't even need a find method (since I would be constructing it with isolated access to each section of to-be-italicized text). I'm not sure why this didn't strike me before. I didn't think about reconstructing the string, I suppose.

---

### Post by smartboyathome on 2010-07-17
Well, I got my portion of code working, even though its not the most efficient of beasts. Either way, it may be able to help you with yours. The code for saving to a file is:

```
def textConvertTo(self, pos=0):
    tmpBuffer = gtk.TextBuffer(self.textTags)
    deserialization = tmpBuffer.register_deserialize_tagset()
    tmpBuffer.deserialize(tmpBuffer, deserialization, tmpBuffer.get_start_iter(), self.textBuffer.serialize(self.textBuffer, "application/x-gtk-text-buffer-rich-text", self.textBuffer.get_start_iter(), self.textBuffer.get_end_iter()))
    boldLock = False
    italLock = False
    undlLock = False
    while pos != tmpBuffer.get_end_iter().get_offset():
        if tmpBuffer.get_iter_at_offset(pos).begins_tag(self.boldTag) and not boldLock:
            tmpBuffer.insert(tmpBuffer.get_iter_at_offset(pos), '<b>')
            pos=pos+3
            boldLock = True
        if tmpBuffer.get_iter_at_offset(pos).begins_tag(self.italTag) and not italLock:
            tmpBuffer.insert(tmpBuffer.get_iter_at_offset(pos), '<i>')
            pos=pos+3
            italLock = True
        if tmpBuffer.get_iter_at_offset(pos).begins_tag(self.undlTag) and not undlLock:
            tmpBuffer.insert(tmpBuffer.get_iter_at_offset(pos), '<u>')
            pos=pos+3
            undlLock = True
        if tmpBuffer.get_iter_at_offset(pos).ends_tag(self.boldTag) and boldLock:
            tmpBuffer.insert(tmpBuffer.get_iter_at_offset(pos), '</b>')
            boldLock = False
        if tmpBuffer.get_iter_at_offset(pos).ends_tag(self.italTag) and italLock:
            tmpBuffer.insert(tmpBuffer.get_iter_at_offset(pos), '</i>')
            italLock = False
        if tmpBuffer.get_iter_at_offset(pos).ends_tag(self.undlTag) and undlLock:
            tmpBuffer.insert(tmpBuffer.get_iter_at_offset(pos), '</u>')
            undlLock = False
        pos=pos+1
    return tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter())
```

Basically, I'm using bbcode (EDIT: Changed to HTML since the bbcode was parsed here, though its still using bbcode in my app) as my format to save as since its pretty easy to use as it is (html is a bit messier). Utilizing this, you could replace the opening and ending tags with anything you wanted easily, and it'd work just the same. The reason there is a tmpBuffer in there is because this code modifies the buffer, and it could potentially ruin whole documents if problems occur, so I'd rather keep the text inside it and ruin the contents of a temporary buffer. To use this, just call textConvertTo() inside a file.write variable, and it should do the rest. :)

Now that I've got that working, I'm going to try creating a loading function, and I'll post the result here. :D

EDIT2: Noticed a bug which didn't order the tags correctly, and corrected. Now seems to work as expected.

---

### Post by kumoshk on 2010-07-17
> **smartboyathome said:**
> Well, I got my portion of code working, even though its not the most efficient of beasts. Either way, it may be able to help you with yours.

Cool. Thanks for sharing. :)

---

### Post by kumoshk on 2010-07-17
All right, I got something that works, although it's still rough, and I need to do a ton of stuff still. It's nice to see those italics for once, after all this time.

I found that I can't add more to the buffer or else it destroys the TextIters, and so I can't add the styles that way. So, I used some integer arrays to capture the text positions and then I turned them into TextIters again after the string is reconstructed (so I'm only reconstructing the string now to get rid of my markup, since I could use the search stuff mentioned above for that&#8212;hopefully I can make a more efficient method later, and maybe just make the markup invisible with a texttag, if that won't leave extra whitespace).

Here's my file-loading function (in Vala):
```
    private void open_file(string filename)
    {
        try
        {
            string text;
            FileUtils.get_contents(filename, out text, null);
            if(text.validate()==false)
            {
                //text=text.to_utf8();
                text=GLib.convert(text, -1, "UTF-8", this.secSet); //secSet is a secondary encoding to try if UTF-8 fails
            }
            TextTagTable ttt=new TextTagTable();
            this.text_view.buffer=new TextBuffer(ttt);
            this.text_view.buffer.text="";
            
            TextTag ttItalic=new TextTag("italic");
            ttItalic.set_property("style", Pango.Style.ITALIC);
            ttt.add(ttItalic);
            
            var markedUpList=text.split("_");
            
            int[] startOffsets=new int[10000]; //Yes, I know, I need something dynamic here; this is temporary
            int[] endOffsets=new int[10000];
            int iOffset=0;
            for(int i=0;i<markedUpList.length;i++)
            {
                if(i%2!=0 && i!=0)
                {
                    TextIter startIter=TextIter();
                    TextIter endIter=TextIter();
                    //Get the iter at the end of the buffer
                    this.text_view.buffer.get_end_iter(out startIter);
                    startOffsets[iOffset]=startIter.get_offset();
                    
                    this.text_view.buffer.text+=markedUpList[i];
                    
                    //Get the iter at the end of the buffer again
                    this.text_view.buffer.get_end_iter(out endIter);
                    endOffsets[iOffset]=endIter.get_offset();
                    
                    //appy the texttag; do this after the buffer is completed
                    //this.text_view.buffer.apply_tag(ttItalic, startIter, endIter);
                    iOffset++;
                }
                else
                {
                    this.text_view.buffer.text+=markedUpList[i];
                }
            }
            for(int i=0;i<=iOffset;i++)
            {
                TextIter startIter=TextIter();
                TextIter endIter=TextIter();
                this.text_view.buffer.get_iter_at_offset(out startIter, startOffsets[i]);
                this.text_view.buffer.get_iter_at_offset(out endIter, endOffsets[i]);
                this.text_view.buffer.apply_tag(ttItalic, startIter, endIter);
            }
            //this.text_view.buffer.text=text;
        }
        catch(Error e)
        {
            stderr.printf("Error: %s", e.message);
        }
    }
```

I should note that the Gutenberg file I mentioned earlier has an odd underscore in there somewhere. I think it was a typo&#8212;so I fixed it in my copy.

The split method is especially inefficient if I want to do multiple kinds of texttags (i.e. I don't want to split it again for bold).

---

### Post by smartboyathome on 2010-07-17
I went about opening a different way, which could be adapted to what you are wanting to do easily enough as long as there are no stray characters which are the same as what you are trying to do. I used the gtk.TextMark feature of a gtk.TextBuffer so that I could keep the same position even after I deleted the tags. Then, I just made a list of the marks as I went since I knew my iters were likely to change a lot. At the very end I set the styles and finally reversed the previous serialization/deserialization command to get it in the current buffer. So far it works great! :D

Here is the code:
```
def textConvertFrom(self, text):
    tmpBuffer = gtk.TextBuffer(self.textTags)
    tmpBuffer.set_text(text)
    boldStarts = []
    boldEnds = []
    italStarts = []
    italEnds = []
    undlStarts = []
    undlEnds = []
    while tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('</u>') > -1:
        tmpPos = tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('<u>')
        undlStarts.append(tmpBuffer.create_mark(None, tmpBuffer.get_iter_at_offset(tmpPos), True))
        tmpBuffer.delete(tmpBuffer.get_iter_at_offset(tmpPos), tmpBuffer.get_iter_at_offset(tmpPos+3))
        tmpPos = tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('</u>')
        undlEnds.append(tmpBuffer.create_mark(None, tmpBuffer.get_iter_at_offset(tmpPos), True))
        tmpBuffer.delete(tmpBuffer.get_iter_at_offset(tmpPos), tmpBuffer.get_iter_at_offset(tmpPos+4))
    while tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('</i>') > -1:
        tmpPos = tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('<i>')
        italStarts.append(tmpBuffer.create_mark(None, tmpBuffer.get_iter_at_offset(tmpPos), True))
        tmpBuffer.delete(tmpBuffer.get_iter_at_offset(tmpPos), tmpBuffer.get_iter_at_offset(tmpPos+3))
        tmpPos = tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('</i>')
        italEnds.append(tmpBuffer.create_mark(None, tmpBuffer.get_iter_at_offset(tmpPos), True))
        tmpBuffer.delete(tmpBuffer.get_iter_at_offset(tmpPos), tmpBuffer.get_iter_at_offset(tmpPos+4))
    while tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('</b>') > -1:
        tmpPos = tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('<b>')
        boldStarts.append(tmpBuffer.create_mark(None, tmpBuffer.get_iter_at_offset(tmpPos), True))
        tmpBuffer.delete(tmpBuffer.get_iter_at_offset(tmpPos), tmpBuffer.get_iter_at_offset(tmpPos+3))
        tmpPos = tmpBuffer.get_text(tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()).find('</b>')
        boldEnds.append(tmpBuffer.create_mark(None, tmpBuffer.get_iter_at_offset(tmpPos), True))
        tmpBuffer.delete(tmpBuffer.get_iter_at_offset(tmpPos), tmpBuffer.get_iter_at_offset(tmpPos+4))
    for start, end in zip(boldStarts, boldEnds):
        tmpBuffer.apply_tag_by_name('bold', tmpBuffer.get_iter_at_mark(start), tmpBuffer.get_iter_at_mark(end))
    for start, end in zip(italStarts, italEnds):
        tmpBuffer.apply_tag_by_name('italic', tmpBuffer.get_iter_at_mark(start), tmpBuffer.get_iter_at_mark(end))
    for start, end in zip(undlStarts, undlEnds):
        tmpBuffer.apply_tag_by_name('underline', tmpBuffer.get_iter_at_mark(start), tmpBuffer.get_iter_at_mark(end))
    self.textBuffer.set_text('')
    deserialization = self.textBuffer.register_deserialize_tagset()
    self.textBuffer.deserialize(self.textBuffer, deserialization, self.textBuffer.get_start_iter(), tmpBuffer.serialize(tmpBuffer, "application/x-gtk-text-buffer-rich-text", tmpBuffer.get_start_iter(), tmpBuffer.get_end_iter()))
```

Now, I asked a question on Stack Overflow about a better way to implement my save function, and was pointed to gtk.TextIter.forward_to_tag_toggle() which looks like it may do exactly what I need! I'm going to rewrite my code and see if I can make it any more efficient. :D

P.S. Sorry I kind of took over your topic, but I feel this may help other people besides just me. :)

---

### Post by kumoshk on 2010-07-17
> **smartboyathome said:**
> P.S. Sorry I kind of took over your topic, but I feel this may help other people besides just me. :)
No, that's great. Post away, and report your findings. A good part of the reason I write a lot of these posts is so there'll be some easy reference out there for people doing a Google search on something of the like. :)

Thanks for the info. That should be helpful.

---

### Post by smartboyathome on 2010-07-17
Cool, thanks. :D

After much frustration, I finally got save reimplemented using forward_to_tag_toggle! Yes, there is a function within a function which is unnecessary, but I didn't want to duplicate the code both inside and outside the while loop. Also, I'm using self variables because it kept erroring out on me saying that I had too few arguments even though they were all the same amount. I wanted to use textmarks because, again, the positions of text were changing and these just make this type of situation very manageable. Finally, the del is there for variable management. ;)

```
def textConvertTo(self, pos=0):
    def apply_tag(self):
        iter = self.tmpBuffer.get_iter_at_mark(self.beginMark)
        if iter.begins_tag(self.boldTag) and not self.boldLock:
            self.tmpBuffer.insert(iter, '[b]')
            self.boldLock = True
        iter = self.tmpBuffer.get_iter_at_mark(self.beginMark)
        if iter.begins_tag(self.italTag) and not self.italLock:
            self.tmpBuffer.insert(iter, '[i]')
            self.italLock = True
        iter = self.tmpBuffer.get_iter_at_mark(self.beginMark)
        if iter.begins_tag(self.undlTag) and not self.undlLock:
            self.tmpBuffer.insert(iter, '[u]')
            self.undlLock = True
        iter = self.tmpBuffer.get_iter_at_mark(self.endMark)
        if iter.ends_tag(self.boldTag) and self.boldLock:
            self.tmpBuffer.insert(iter, '[/b]')
            self.boldLock = False
        iter = self.tmpBuffer.get_iter_at_mark(self.endMark)
        if iter.ends_tag(self.italTag) and self.italLock:
            self.tmpBuffer.insert(iter, '[/i]')
            self.italLock = False
        iter = self.tmpBuffer.get_iter_at_mark(self.endMark)
        if iter.ends_tag(self.undlTag) and self.undlLock:
            self.tmpBuffer.insert(iter, '[/u]')
            self.undlLock = False
    self.tmpBuffer = gtk.TextBuffer(self.textTags)
    deserialization = self.tmpBuffer.register_deserialize_tagset()
    self.tmpBuffer.deserialize(self.tmpBuffer, deserialization, self.tmpBuffer.get_start_iter(), self.textBuffer.serialize(self.textBuffer, "application/x-gtk-text-buffer-rich-text", self.textBuffer.get_start_iter(), self.textBuffer.get_end_iter()))
    self.boldLock = False
    self.italLock = False
    self.undlLock = False
    self.beginMark = self.tmpBuffer.create_mark(None, self.tmpBuffer.get_start_iter(), False)
    self.endMark = self.tmpBuffer.create_mark(None, self.tmpBuffer.get_start_iter(), True)
    apply_tag(self)
    tmpIter = self.tmpBuffer.get_iter_at_mark(self.beginMark)
    tmpVar = tmpIter.forward_to_tag_toggle(None)
    while tmpVar:
        self.beginMark = self.tmpBuffer.create_mark(None, tmpIter, False)
        self.endMark = self.tmpBuffer.create_mark(None, tmpIter, True)
        apply_tag(self)
        tmpIter = self.tmpBuffer.get_iter_at_mark(self.endMark)
        tmpVar = tmpIter.forward_to_tag_toggle(None)
    text = self.tmpBuffer.get_text(self.tmpBuffer.get_start_iter(), self.tmpBuffer.get_end_iter())
    del(self.beginMark, self.endMark, self.boldLock, self.italLock, self.undlLock, self.tmpBuffer)
    return text
```

---

### Post by kumoshk on 2010-07-17
Cool. Thanks again for that.

> **smartboyathome said:**
> Also, I'm using self variables because it kept erroring out on me saying that I had too few arguments even though they were all the same amount.

What class is the object that self refers to an instance of? That should help me to understand your code a little better.

---

### Post by smartboyathome on 2010-07-18
> **kumoshk said:**
> What class is the object that self refers to an instance of? That should help me to understand your code a little better.

self is just a supervariable I guess you would call it (even though I'm getting pretty good at python, I still don't know all the names). Basically, it refers to all the global variables under MainWindow, and I use them so I can communicate between different functions (defs) since variables set in functions are lost after the function is run and only available within the function. This includes when running a function within a function (as seen here with apply_tag).

---

### Post by dannym on 2010-12-05
First, thanks for this thread, I found how to do deserialization of a textbuffer. Thanks.

So:

```

class MainWindow(object):
    def textConvertTo(self, pos=0):
        ...
        return self.whatever

```

self has no special meaning. It's just the name of the first argument.

```

class Foo(object):
    def textConvertTo(stuff, pos=0):
        ...
        return stuff.whatever

```

Works as well.

Python has a special syntax to access member functions of classes:

self.textConvertTo(pos)

is equal to

MainWindow.textConvertTo(self, pos)

if self is an instance of MainWindow.

Again, the word "self" has no special meaning. It does that always: prepend a (new) first argument. Again, it doesn't matter what it is called:

foo.textConvertTo(pos)

is equal to

MainWindow.textConvertTo(foo, pos)

if foo is an instance of MainWindow.

> Basically, it refers to all the global variables under MainWindow 

member variables in MainWindow

>, and I use them so I can communicate between different functions (defs) since variables set in functions are lost after the function is run and only available within the function. 

Except when they are explicitly returned or passed on or in the enclosing scope of the function.

> This includes [variables set in the outer function] when running a function within a function (as seen here with apply_tag). 

No it doesn't. It wouldn't make any sense to have functions within a function it that were so.

What doesn't work is _changing_ values of variables that are in the outer functions without specifying the keyword "nonlocal".

---

### Post by smartboyathome on 2010-12-05
This is an older reply for me, and I realize that its not the best explanation, indeed you are correct on all points. Since that I learned a lot more (including having actually taken a programming class), and if anyone wants to see the latest version of the code they can go to [here](http://github.com/smartboyathome/SmartTE)

---

