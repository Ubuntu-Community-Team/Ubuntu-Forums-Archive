---
title: "Very Basic Question about Quickly"
date: 2010-05-31
forum: Programming Talk
---

### Post by DrShrinker on 2010-05-31
I am new to Linux and Python programming.  I watched all of the YouTube tutorials on Quickly and went through the user guide that ships with it.

I'm trying to create a simple "hello world" program that changes a label's text to "hello world" when a button is clicked.  I've been stuck for hours.

Here's what I did:


[LIST]
[*]I created a new Quickly program titled "helloworld"
[/LIST]
> quickly create ubuntu-application helloworldI changed to the directory and ran Glade:
> quickly design
[LIST]
[*]I deleted image1 and replaced it with a button (button1)
[/LIST]

[LIST]
[*]I added an event handler (signal) for on_button1_clicked
[/LIST]

[LIST]
[*]I saved the design in Glade and ran Quickly edit
[/LIST]

[LIST]
[*]Under the on_destroy function, I wrote the following function:
[/LIST]

>     def on_button1_clicked(self, widget, data=None):
        # called when button clicked
        label1.label = 'hello'And I got the error:

> Traceback (most recent call last):
  File "bin/helloworld", line 117, in on_button1_clicked
    label1.label = 'hello'
NameError: global name 'label1' is not definedAlso, in reviewing the code in the editor, I thought I'd try changing the above to self.label1.label = 'hello' but got the error:

>   File "bin/helloworld", line 117, in on_button1_clicked
    self.label1.label = 'hello'
AttributeError: 'HelloworldWindow' object has no attribute 'label1'I'm obviously missing something very basic.  Could you please point me  in the right direction?  Perhaps there's a basic tutorial out there that  I cannot find.

Thanks.

---

### Post by DrShrinker on 2010-05-31
I figured it out. 

First, I added a line of code after the following comment:

```
        # Code for other initialization actions should be added here.
        self.label1 = self.builder.get_object('label1')
```Then I added the following function, right after the on_destroy function:
```

    def on_button1_clicked(self, widget, data=None):
        self.label1.set_text("hello world!")
```

---

