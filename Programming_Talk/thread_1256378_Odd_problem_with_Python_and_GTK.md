---
title: "Odd problem with Python and GTK"
date: 2009-09-02
forum: Programming Talk
---

### Post by M4rotku on 2009-09-02
Hey guys,

I'm writing a program in python using gtk via glade.  The program at this point just prompts for a few settings on how a video track should be ripped and for the number of tracks to rip from a dvd.  On the next tab of the program, it prompts for the titles of the tracks.  I have the gtkspinbutton which sets the number of tracks set off a signal that is supposed to change the number of title entries that the second tab shows.

However, The function which the signal executes doesn't change the number of titles unless one has already looked at the title tab.  Otherwise, it just shows the first title entry spot (which is there by default) and nothing else.

Does the tab have to be opened before the rest of the program can access its widgets?  How can I set up the signal and function correctly so that one does not have to switch the tabs back and forth for it to work?

I am uploading the .py file and the .glade file within an archive since .glade's are not uploadable in themselves.

Any help is very much appreciated.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-09-03
bump

---

### Post by days_of_ruin on 2009-09-03
You should not create the entries in the glade file, you should create them on demand in pygtk, also libglade is deprecated use gtk.Builder instead. I modified your code and glade file and it now works fine.

---

### Post by M4rotku on 2009-09-05
Wow, thanks.  That looks like it was a lot of work.  It does seem advantageous to create them with pygtk and I will probably change my code to do so.  However, I'm still wondering if there is an explanation for why creating them with glade wasn't working.

I was originally wanting to create them with pygtk, but I didn't understand the documentation, so your example on that will be extremely helpful.

---

### Post by M4rotku on 2009-09-10
Hey, I was looking at the example that you gave me and when I was trying to get my packing to work properly I realized that they glade file that you posted as more options under the packing tab than the one that I was using and that you used these extra options to create the desired spacing.  Can you tell me how you got those extra options?  Is it a newer version of glade?

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-09-11
bump

---

### Post by days_of_ruin on 2009-09-11
> **M4rotku said:**
> Hey, I was looking at the example that you gave me and when I was trying to get my packing to work properly I realized that they glade file that you posted as more options under the packing tab than the one that I was using and that you used these extra options to create the desired spacing.  Can you tell me how you got those extra options?  Is it a newer version of glade?

Much thanks,
M4rotku

What options are you talking about? I am using Glade 3.6.3 btw.

---

### Post by M4rotku on 2009-09-12
I think it'll just be easiest to upload a pic of each tab.

The ones that you edited in your version are the ones that I need to be able to access in mine.  It's easy to tell because they are bolded.

---

### Post by days_of_ruin on 2009-09-12
> **M4rotku said:**
> I think it'll just be easiest to upload a pic of each tab.

The ones that you edited in your version are the ones that I need to be able to access in mine.  It's easy to tell because they are bolded.

What format are you saving the glade file as? Be sure to use GtkBuilder.

---

### Post by M4rotku on 2009-09-13
It is currently in GtkBuilder, but I originally created the file with libglade so I'm wondering if those options forgot to switch over.

---

### Post by M4rotku on 2009-09-15
bump

---

### Post by M4rotku on 2009-09-16
I have a quick question.  When the new labels and entry boxes are created by the pygtk commands, what are their names?  Are the first ones still label1 and entry1 and so on?  Does pygtk name them automatically or will they all somehow be called the same thing?  I need to know so that I can get the episode titles out of the entry boxes.

---

### Post by days_of_ruin on 2009-09-17
> **M4rotku said:**
> I have a quick question.  When the new labels and entry boxes are created by the pygtk commands, what are their names?  Are the first ones still label1 and entry1 and so on?  Does pygtk name them automatically or will they all somehow be called the same thing?  I need to know so that I can get the episode titles out of the entry boxes.

The don't have any name.

---

### Post by M4rotku on 2009-09-17
So how would I get the episode names from them?  How do I access what the user inputs in the text entries?  I'm hoping that there is some way because if there were then it would make things very easy for me.

---

### Post by days_of_ruin on 2009-09-17
Just create a list that holds all of the entries as you create them.

```
        self.entries = []

        ## remove all entries
        children = [child for child in self.entry_box.get_children()]
        for child in children:
            self.entry_box.remove(child)

        for count in range(1, number + 1): 

            label = gtk.Label(str(count))
            entry = gtk.Entry()
            self.entries.append(entry)
   
```

---

