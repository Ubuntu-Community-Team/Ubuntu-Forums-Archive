---
title: "Need help with Instiki"
date: 2006-09-21
forum: Programming Talk
---

### Post by Blacktalon on 2006-09-21
Hey everyone,

Yeah I found an Instiki site, and I pretty much built most of the code I need for my Instiki but the only problem is I can't figure out a way to how to implement a correct Destroy method...here's what I have so far for the destroy method

def destroy
  Page.find(params[:id]).destroy
  redirect_to :action => 'index'
end

I keep getting a error when every i click on the destroy button says that there is no id for the page that I created and tried to destroy.  Anyone got any ideas?  or do you need me to post more of the code for you to see what's going on?

And before anyone suggests I have went out looking at others code to see what I am doing wrong, and alot of people don't seem to have a destroy option for there Instiki.  So no I am not trying to re-Invent the wheel.


Thanks
  ~BT

---

### Post by Blacktalon on 2006-09-22
*bump*

---

