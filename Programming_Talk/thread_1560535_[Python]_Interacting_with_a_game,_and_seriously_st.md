---
title: "[Python] Interacting with a game, and seriously stuck."
date: 2010-08-25
forum: Programming Talk
---

### Post by Asday on 2010-08-25
It might just be because it's half 5 in the morning, but this looks absolutely bulletproof-perfect to me, but for some reason, the game is returning me the same page each time.

[PHP]def readin(sesh,int_pages,tup_range=False):
    x=0
    if tup_range:
        x=tup_range[0]
        int_pages=tup_range[1]-tup_range[0]
    y=x
    pages=[]
    excepd=[]
    for page in xrange(int_pages):
        print("fetching page %d of %d"%(page+x+1-y,int_pages))
        while True:
            try:
                print(page+x+1)
                p=urllib.urlopen("http://www.darkthrone.com/userlist/attack?dt_session_id1=%s&amp;page=%d"#&amp;dt_session_id1=%s"
                                 %(sesh,page+x+1))#,sesh))
                break
            except:
                print("failed page %d, retrying"%(page+x+1),
                      traceback.print_exc())
                excepd.append(traceback.print_exc())
        pages.append(p.read())
    return(pages,excepd)[/PHP]

This stuff I'm poking around with is all completely new to me, so it may be extremely obvious, or completely obscure; and as such, I have no idea how much information to give, or indeed what information to give.

Thank you for your patience.

EDIT:  Title.

---

### Post by Asday on 2010-08-25
Doublepost to show solution.

With some help from the folks over at 4chan, (surprisingly), I found it was a very simple and very stupid error.

I'd been writing this program line by line in the interactive interpreter, and each line was based on the results of the last one, so when I wanted to go to page 8, for instance, I pulled up a page I knew had the link to a page by number, and then swapped out the number.

Thing is, **_&amp; is an ampersand in html, but just & is an ampersand in http._**

Yes, I was that blind.

---

