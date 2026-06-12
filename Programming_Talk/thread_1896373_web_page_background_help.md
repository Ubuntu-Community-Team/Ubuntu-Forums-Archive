---
title: "web page background help"
date: 2011-12-16
forum: Programming Talk
---

### Post by &lt;/o=Dog&gt; on 2011-12-16
hi,
i have put a small background image an my basic web page as i am just beginning to learn how to do all this.
I have inserted the image using css and have managed to it put on the left of the page at the top, i've set it as fixed as i dont want it to scroll with the rest of the page, i have repeated on the y axis so it goes down the page, but i have an empty void on the right side of my page, i was wondering if there is a way to do this so that the image does the same on both sides the code i have used is below:-

 <style type="text/css" media="all">
                body {
                        font: 100%/1.5 arial, helvetica, sans-serif;
                        color: black;
                        background-color: white;
                        background-image: url();
                        background-attachment: fixed;
                        background-repeat: repeat-y;
                }
basically i want the same image going down both left and right sides but not scrolling with rest of the page
any help would be much appreciated thanx

---

### Post by sandyd on 2011-12-16
> **</o=Dog> said:**
> hi,
i have put a small background image an my basic web page as i am just beginning to learn how to do all this.
I have inserted the image using css and have managed to it put on the left of the page at the top, i've set it as fixed as i dont want it to scroll with the rest of the page, i have repeated on the y axis so it goes down the page, but i have an empty void on the right side of my page, i was wondering if there is a way to do this so that the image does the same on both sides the code i have used is below:-

 <style type="text/css" media="all">
                body {
                        font: 100%/1.5 arial, helvetica, sans-serif;
                        color: black;
                        background-color: white;
                        background-image: url();
                        background-attachment: fixed;
                        background-repeat: repeat;
                }
basically i want the same image going down both left and right sides but not scrolling with rest of the page
any help would be much appreciated thanx
```

<style type="text/css" media="all">
                body {
                        font: 100%/1.5 arial, helvetica, sans-serif;
                        color: black;
                        background-color: white;
                        background-image: url();
                        background-attachment: fixed;
                        background-repeat: repeat;
                }
```

---

### Post by mörgæs on 2011-12-16
Moved to Programming Talk.

---

### Post by &lt;/o=Dog&gt; on 2011-12-16
thanx for the quick reply but i have tried the repeat, option but that covers the whole page, i would like it just to go down the left y-axis and right y-axis not in the middle as well i have seen it done but cant figure out how to go about it, i was wondering if it possible to mix up the commands so it would be somthing like this:-

background-repeat: repeat-y;
                        background-position: right top;left top
to get the effect that i am looking for

---

### Post by &lt;/o=Dog&gt; on 2011-12-16
i have a file server using xubuntu, i have a proxy on debian and use ubuntu as my main mechine, i have also tried mint puppy linux and kubuntu they are all good for doing different things i find

---

### Post by epicoder on 2011-12-17
Use the code posted by sandyd, then put your main content in a div with this styling:
```
div.main {
    background-color:white;
    margin: 0px [width of your background image];
}
```
Then use background-repeat:repeat; on your main body.

---

### Post by dazman19 on 2011-12-17
looks like this has been answered for you. But one thing that I will highly recommend is a tool like firebug for Firefox. Or use the developer tools in Google chrome. They can tell you how the CSS is computed and its easier to figure out what bits of CSS are overriding other bits etc. 

You will probably want to look at a couple of youtube videos on how to use firebug. But Its definitely worth the download if you are not already using it.

---

