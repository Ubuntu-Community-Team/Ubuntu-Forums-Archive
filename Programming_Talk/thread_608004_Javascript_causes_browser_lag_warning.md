---
title: "Javascript causes browser lag warning"
date: 2007-11-09
forum: Programming Talk
---

### Post by exhume on 2007-11-09
Ok, so I have been dabbling with Javascript for a long time now, but have never used it for something like a picture fade/change effect before. I have really only used it for its redirect features and to animate buttons. I was asked to incorporate the fade/change effect mentioned above into the redesign of a website I work on and after a few hours had what I wanted. The problem is that sometimes when you try to open the page in a browser, the browser complains about the script running slowly or not responding. If you simply close the page and reopen it it runs just fine, but I personally don't find that warning acceptable. I am posting my code below and was wondering if anyone could find a way to make it faster or knows the cause of the browsers complaint. Thanks.

```

var index= 0
var imgarry= new Array()
var t
var i
var t2
var t3
var op=10
var j=0

function preload()
{
  //max image size is 400 by 125
  imgarry[0]= new Image(100,125);
  imgarry[0].src="images/scroll/1.jpg";

  imgarry[1]= new Image(100,125);
  imgarry[1].src="images/scroll/2.jpg";

 
  while (j==0)
  {
    if(imgarry[0].complete && imgarry[1].complete)
    {
      starttime();
      j=1;
    }
  }
}


function setop()
{
  imgbar.style.opacity= op/10
  imgbar.style.filter= 'alpha(opacity=' +op*10+ ')'
}

function fade()
{
  setop()
  if(op==0)
  {
    clearTimeout(t2)
    fwd()
  }
  else
  {
    op--
    t2=setTimeout("fade()", 100)
  }
}

function fwd()
{
  if(index==1)
  {
    index=0
    document.imgbar.src= imgarry[index].src
  }
  
  else
  {
    index++
    document.imgbar.src= imgarry[index].src
  }
  appear()
}

function appear()
{
  setop()
  if(op==10)
  {
    clearTimeout(t2)
  }
  else
  {
    op++
    t2=setTimeout("appear()", 100)
  }
}

function starttime()
{
  fade()
  t=setTimeout("starttime()", 8000)
}


```

The HTML code for the img that is being rotated contains onload="preload()"

Thanks again for any help you can give me

---

### Post by smartbei on 2007-11-10
Interesting code by the way. Very...Functional :D.

The problem is this part of your code:
```

  while (j==0)
  {
    if(imgarry[0].complete && imgarry[1].complete)
    {
      starttime();
      j=1;
    }
  }
```
You have a (from the browser's perspective) a possibly infinate loop. Since all you are trying to do is figure out when the two images have loaded, you should use the onLoad event handler. See [http://articles.techrepublic.com.com/5100-22-5214317.html](http://articles.techrepublic.com.com/5100-22-5214317.html) for more 
information.

Since after the first time you load the page the images are cached on the user's computer, a refresh or a second visit will not have the problem.

Just by the way, function fwd could be replaced by:
```

function fwd()
{
  index=index^1
  document.imgbar.src= imgarry[index].src
  appear()
}
```
Since we just want index to toggle between 0 and 1, it is simpler to just bitwise xor its current state with 1.

---

### Post by exhume on 2007-11-10
Thanks for the help, but it wont actually always be toggling between 0 and 1. I just didn't feel like scraping together more than 2 pictures to test it. It will probably be running more like 8 once it actually goes live.

---

### Post by smartbei on 2007-11-11
I see. Well, glad I could help.

Still,
```
document.imgbar.src= imgarry[index].src
```
can come out of the if/else block.

---

### Post by kefler on 2007-11-15
I don't THINK your script will EVER exit.

When you load an image, say..

var img = new Image
img.src = "test.jpg";

if you alert(img.src) it wont return "test.jpg", it'll return "http://yourjost/folder/test.jpg" either way, I THINK you're going about it the wrong way.

checking to see if a variable holds a value after specifically assigning it a value will always return true(with the slight exception in this case where the value gets slightly modified)

what you should do is loop it and check for the width/height of the image in the img object, and if it returns one, then continue with the other stuff.
(don't set the width/height when you make a new image object that way it gets dynamically set when the image is FINISHED loading.)

> function iloadImage(image) {
    if(!document.imageArray) { 
        var document.imageArray = new Array; //create a global image array
        var document.imageArray[0] = new Image;

        imageArray[0].src = "test.jpg";
        setTimeout("iloadImage("+image+")", 10);
        //this timeout is to stop firefox from catching an "infinite loop"
    } else {
        for(i=0;i<imageArray.length;i++) {
            var basename = "";

            if(imageArray[i].match(/{image}/gi) { //make sure to only check the status of the image it's currently trying to load.
            //(sorry i don't know the exact syntax of the javascript match function)
                if(imageArray[i].offsetWidth) { //fetch the width of the image object, if there is one, the image has finished loading
                    //image has finished loading
                    //some code to do stuff.
                } else {
                    setTimeout("iloadImage("+image+")", 10);
                    //this timeout is to stop firefox from catching an "infinite loop"
                }
            } else {
                setTimeout("iloadImage("+image+")", 10);
                //this timeout is to stop firefox from catching an "infinite loop"
            }
        }
    }
}

this function theoretically works as is. I know the theory itself works for loading images and waiting for them to finish since I used something like it for my old site.  sorry if i've misread your post and you've already done this. Don't ask why the setTimeout gets past the firefox infinite loop catch but it does, technically it should ignore the timeout since it's irrelevant in it's check. My guess is, the stack overflow and infinite loop error messages are the exact same thing.

Yes there is a difference between infinite loop and stack overflow.

while 1 {
// some code and no exit statement
} is an infinite loop but should never return a stack overflow

function someName() {
// code to do some stuff
someName();
} is an infinite loop that will return a stack overflow because it will never reach the closing curly bracket and thus piling up the past } instructions in the stack and the stack can only hold so many items.

---

### Post by smartbei on 2007-11-15
@kefler: What are you talking about? Where in his code does he compare the src? And why do you think that he will recieve a stack overflow/infinite loop error? The only place he has anything close to either is the while loop in the preload function. Since he has probably changed that to being event-based as I recommended, that would not be a problem anymore. A stack overflow does not make sense, as he is **not** doing recursion. A timeout returns immediately, exiting the function and calling it again after the time has gone by.

Sorry if that sounded harsh but I really am not sure what you are talking about :p.

---

### Post by LaRoza on 2007-11-15
@kefler Use Code tags, or php tags when posting code to keep the formatting

---

### Post by ThinkBuntu on 2007-11-15
Making a fading slideshow from scratch is terrible. I once tried to do this and, although there was absolutely nothing wrong with my script, opacity would jump all over the place. In the end, I gave up and simply adapted this solid script from Dynamic Drive to my needs:

[http://www.dynamicdrive.com/dynamicindex14/fadeinslideshow.htm](http://www.dynamicdrive.com/dynamicindex14/fadeinslideshow.htm)

---

### Post by smartbei on 2007-11-15
Yes, I was actually going to recommend something like [JQuery]("http://jquery.com/"), but since the OP already had source... (and JQuery is a bit heavy if all you want to do is fade in and out ads).

---

### Post by kefler on 2007-11-16
Oh, haha thanks LaRoza didn't even notice the code tags, was wondering if there was a way to keep the formating aside from using &.nbsp's :lolflag:

---

### Post by DvX on 2007-11-16
thanks =;

---

