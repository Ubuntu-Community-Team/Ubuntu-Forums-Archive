---
title: "Python multithreading question"
date: 2009-11-15
forum: Programming Talk
---

### Post by rob86 on 2009-11-15
When I make a function like

def func(): return 'value'

and I do 

print thread.start_new_thread(func,(),) 

It returns a strange number instead of 'value', is there any way to return the actual return value of the function?

---

### Post by 0cton on 2009-11-15
can you provide some actual code? your post is ambiguous.

---

### Post by Arndt on 2009-11-15
> **rob86 said:**
> When I make a function like

def func(): return 'value'

and I do 

print thread.start_new_thread(func,(),) 

It returns a strange number instead of 'value', is there any way to return the actual return value of the function?

It can't return 'value', because that would mean that the caller has to wait while the thread runs to completion, which would make the whole thread concept meaningless. The strange number is something identifying the thread.

You can send an object as an argument to 'func' and let 'func' write into it. Then wait for the thread to finish and inspect the object. (I don't know if this is the best way.)

---

### Post by rob86 on 2009-11-15
I get what you're saying Arndt. Maybe I was trying to do something with multithreading that isn't supposed to be done. 

It's kind of hard to post the working code without pasting a large bunch of text..  but here's a (non working) bit of what I'm trying to do..

This is a Tkinter app that sends email via smtp.. this part is trying to change the statusbar. The first line tells the statusbar to flash/blink (this is a custom method I made). That method makes something on the statusbar flash, but originally it holds up the code from running, and instead of flashing to show that it's sending e-mail, it flashes, and then sends email.

So I added the new thread. This still doesn't work, because once the smtp_backend.sendMail function (in another module) runs, the GUI completely freezes up until the function completes, 

smtp_backend_sendMail normally returns "True or 1" when it finishes without error, which should  execute the if body. I could fix this easily by starting a new thread for this as well (I tried it, and it fixes the gui freezing issue. The problem is, I would like to have some confirmation that smtp_backend.sendMail actually completed without error, and since thread's don't return a value, I'm not sure how to do that.

```

        thread.start_new_thread(self.statusbar._flash, (50,0) )
        if (smtp_backend.sendMail(self.subject,self.body,self.recipient) == 1):
            print 'The e-mail sent successfully.'
        else:
            print 'Something went wrong!!'


```

---

