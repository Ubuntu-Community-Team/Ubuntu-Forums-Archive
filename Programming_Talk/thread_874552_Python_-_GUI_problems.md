---
title: "Python - GUI problems"
date: 2008-07-30
forum: Programming Talk
---

### Post by aktiwers on 2008-07-30
Hey Guys,

I'm still learning python and I hit another wall. I am trying to write small programs just for the practice of it and I keep getting an error here. I will post the part of the code that gives me error below:

[php] 
    self.download = Button(self, text="Download", command=self.Single)
    self.download.grid(row=2, column=3)

def Single(self):
     # Download single file
         l = Entry.get(self.url)
         command = "wget " + l
         os.system(command)
[/php]The error I get is:
> Traceback (most recent call last):
  File "PyWget.py", line 55, in ?
    guiFrame = GUIFramework()
  File "PyWget.py", line 28, in __init__
    self.CreateWidgets()
  File "PyWget.py", line 43, in CreateWidgets
    self.download = Button(self, text="Download", command=self.Single)
AttributeError: GUIFramework instance has no attribute 'Single'Basically I am just trying to build a very simple GUI for wget.

Is this error because the button somehow does not see my Single function or?

Let me know if you need more info, this has been troubling me for 2 hours now, and I have used similar e code in another GUI I made without any problem :(

If I remove the command=self.Single from the Button, I get that 'l' is not globally defined error in the Single function..

---

### Post by aktiwers on 2008-07-30
Ok I fixed it with:
[php]
self.download = Button(self, text="Download", command=lambda:Single(self))
self.download.grid(row=2, column=3)[/php]Please let know if this is the right approach.
Thanks :)

---

### Post by loell on 2008-07-30
i thought it was suppose to be

```
self.download = Button(self, text="Download", command=self.Single[COLOR="Red"]()[/COLOR])
```

if lambda worked, then its fine ;)

oh, you can just initialize l as  l="" before entry get.

---

### Post by ib.lundgren on 2008-07-30
To me it looks like you have by mistake indented you code wrong so the Single function falls outside your "GUIFramework" class. 

```
self.download = Button(self, text="Download", command=self.Single)
```

The original looks good, it should not be self.Single() since you want to send a function, if you add the parenthesis it becomes a function call.

```


class GUIFramework:

   def __init__(self):

      self.download = Button(self, text="Download", command=self.Single)
 
   # Correctly indented
   def Single(self):
      # Download

# Wrongly indented, this is an independet function and not a method of GUI Framework
def Single(self):
   # Download


```

---

### Post by aktiwers on 2008-07-30
> **ib.lundgren said:**
> To me it looks like you have by mistake indented you code wrong so the Single function falls outside your "GUIFramework" class. 

```
self.download = Button(self, text="Download", command=self.Single)
```The original looks good, it should not be self.Single() since you want to send a function, if you add the parenthesis it becomes a function call.

```


class GUIFramework:

   def __init__(self):

      self.download = Button(self, text="Download", command=self.Single)
 
   # Correctly indented
   def Single(self):
      # Download

# Wrongly indented, this is an independet function and not a method of GUI Framework
def Single(self):
   # Download


```

Thanks for the input! The tutorials I have read also say command=self.Single should be the way to do it. But it throws that error at me. The lambda thing fixes it though it does not look to be the real way to do it. I also thought it would be the indentation that was wrong, but it is, and has been all the time, like you state should be currect. 

The strange thing is I have another program where I use the same indentation and it works fine.

Now it looks like this:
[php]
class GUIFramework:

   . . .

       # Laver knap
        self.download = Button(self, text="Download", command=lambda:Single(self))
        self.download.grid(row=2, column=3)
    
    def full(self):
    #Download full site
        l = Entry.get(self.url)
        command = "wget -r " + l
        os.system(command)
         
    def Single(self):
     # Download single file
        l = Entry.get(self.url)
        command = "wget " + l
        os.system(command)
     
    . . .
       [/php]And it works fine with the command=lambda:function(self) but not the way the guides/tutorials suggests command=self.function

Strange, but if anyone can figure it out it would be a great help, as I want to learn the "right" way to do this, even though this way also works.

Thanks!

---

