---
title: "Java program advice"
date: 2011-05-05
forum: Programming Talk
---

### Post by alexmoca on 2011-05-05
I am making a program which allows me to save the text messages that I like the most. :) Simply type the message and click save and then load back it whenever you want.

The problem is that I am not sure how to store them [the text messages] on my computer. Saving every one of them in a separate file and then loading them back in the program from their own files doesn't seem elegant at all. There must be another way.

Any suggestions?

---

### Post by r-senior on 2011-05-05
If it's just simple text you could use a [java.util.Properties](http://download.oracle.com/javase/6/docs/api/java/util/Properties.html) object, which is easy to load/save and you can edit the [.properies file](http://en.wikipedia.org/wiki/.properties) with a text editor if you need to. It's basically name/value pairs so your file would be something like this:

```

thanks = Thank you!
nothanks = Very kind of you, but no thanks

```

You can also load/save properties to an XML format using java.util.Properties if you prefer.

Other alternatives would be another format that you parse, e.g. CSV or your own format. Or you could use XML. Or a database. I'd probably go for Properties if it's a simple requirement and likely to stay that way.

---

### Post by cgroza on 2011-05-05
If you want a single unified file, use the XML format. It will allow you to save extra info about the text later if you want to improve it.

---

### Post by heyandy889 on 2011-05-05
Maybe just use an Excel... I mean, ahem, an Open Office spreadsheet. I think that might be the highest reward for the least amount of work.

Oh, you wanted it in Java? Um . . . well, sounds like XML might be a good way to go. Or, use a pre-built "database" like MySQL. Or, dive into the heady world of data structures with linked lists, hash tables and trees [http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list)

---

### Post by alexmoca on 2011-06-22
Thanks everybody for your suggestions! I have been busy lately with Uni and exams, thank God it's all over for this year!

I am trying the XML approach right now using the XOM library. So basically I should store everything in this huge XML file which looks like this:

```

<root>

<message id="some_id">
    <sender>
        <name>John</name>
        <telephone>07222</telephone>
    </sender>
    <receiver>
        <name>Gary</name>
        <telephone>07233322</telephone>
    </receiver>
    <text>Hey, mate!</text>
</message>

<message id="another_id">
    <sender>
        <name>John2</name>
        <telephone>0722332</telephone>
    </sender>
    <receiver>
        <name>Gary2</name>
        <telephone>07233322</telephone>
    </receiver>
    <text>Cool!</text>
</message>

</root>

```

Is this a good starting point?

---

### Post by cgroza on 2011-06-22
Yes, you can always improve the XML tree if you have new ideas. Also, do not use it now to store your messages, because if you add a new attribute in your XML tree, you may need to rebuild the whole file.

---

### Post by alexmoca on 2011-06-25
> **cgroza said:**
> Yes, you can always improve the XML tree if you have new ideas. Also, **do not use it now to store your messages, because if you add a new attribute in your XML tree, you may need to rebuild the whole file.**

Great observation, cgroza, thank you! Then what do you suggest if you don't recommend the XML approach?

---

### Post by cgroza on 2011-06-26
> **alexmoca said:**
> Great observation, cgroza, thank you! Then what do you suggest if you don't recommend the XML approach?
I do recommend it, just don't start creating a text database until your are sure that the XML format reached it's final form.
I think XML is the best approach to this.

---

### Post by Some Penguin on 2011-06-26
How you should store them rather strongly depends upon how you'll access and modify them.

---

### Post by Petrolea on 2011-06-27
I'd go for a database but that's a bit more complicated. But once you set it up it's easy to add/delete data. I recommend SQLite for local database or MySQL if you want to access it from somewhere else also.

---

### Post by cgroza on 2011-06-27
> **Petrolea said:**
> I'd go for a database but that's a bit more complicated. But once you set it up it's easy to add/delete data. I recommend SQLite for local database or MySQL if you want to access it from somewhere else also.
What if he changes computers? It is much easier to copy and paste a XML file.
Plus, his program can have an import and export feature which makes this task a lot more easier.

---

### Post by PaulM1985 on 2011-06-27
> **cgroza said:**
> What if he changes computers?

I just googled backing up and restoring SQLite.  Seems pretty easy, almost as easy as copying and pasting a file.

SQLite might be worth looking into.

Paul

---

### Post by alexmoca on 2011-06-29
Thanks everyone for your input! I will go for the XML approach for now. I may consider the database option when my application works! :)

---

