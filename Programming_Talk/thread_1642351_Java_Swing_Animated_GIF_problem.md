---
title: "Java Swing: Animated GIF problem"
date: 2010-12-10
forum: Programming Talk
---

### Post by Nytram on 2010-12-10
Hi guys,

I'm new to Java so this may be a simple problem, but I've searched for a solution and had no luck.

I'm having trouble displaying a GIF in a JLabel in a certain way. I want my program to display the animated GIF and have the image run thru the animation 1 time only. Then I want successive displays of the image to also show it the same way - ie I don't want it to loop forever.

This is what is actually happening at the moment - on first display of the image it animates 1 time only, which is good. But when I display the image further times there is no animation, just a static frame.

(Basically I want to display an animated tick mark every time a user get's a correct answer.)

I'm not sure I've explained it very well, so let me know if you want further info.

Here are some code snippets im using:

Initialise JLabel
[PHP]
		ImageIcon pic=new ImageIcon("result.png");		
		resultImage=new JLabel(pic);
		boxMain.add(resultImage);
[/PHP]

Display new image
[PHP]
ImageIcon resultIcon=new ImageIcon("tickAnim2.gif");
resultImage.setIcon(resultIcon);
[/PHP]

Thanks for any help.

---

### Post by t1497f35 on 2010-12-10
I'd just make the images show up in sequence, possibly using a custom class (extend a JPanel with a custom paint() method, or extend a JLabel) which would take like 5 minutes to create. But for that you'd need separate image files.
Other than that, I'd suggest you post a working example of what you're doing cause if people can reproduce your issue it usually helps leveraging your issue quicker. Also, posting the animated gif or images would be welcome too.

---

### Post by Nytram on 2010-12-10
Thanks for the reply t1497f35. It's a bit late here and I don't have the animations completed yet, so tomorrow I'll put together a prototype gif and make a fuller reply to your post.

---

### Post by Nytram on 2010-12-11
I'm new to Java and I'm not sure I understand how to create a custom paint method. If I were to display the images in sequence, would that not lock up my program until the animation was complete?

I've attached a mockup of the tick gif id like to use.

My program puts a series of questions to the user, and each time s/he gets a correct answer i'd like to display my animated tick gif.

The problem im having is that the animation only plays the 1st time i show the image, on successive displays of the gif it just shows a static picture.

[ATTACH]178144[/ATTACH]

---

### Post by t1497f35 on 2010-12-11
Example.zip contains "App.jar" which is a demonstration of an animated JLabel which runs when the JButton is clicked (you can customize it to trigger the event whenever you need) and the folder "App" is the NetBeans project with the source code.

If you want the animation to go faster or slower just change "100" from
th.sleep(100);
from the class AnimatedIcon to the value you need.

---

### Post by Nytram on 2010-12-11
Your program works exactly the way i was looking for, thanks t149.

I was hoping the solution would be something simple, to match my level with Java, such as a few lines of code.

As it is, ill take some time to go thru your code, but will probably end up going with static images, as i find it far simpler.

Thanks again for the code.

---

### Post by t1497f35 on 2010-12-12
The class that matters is AnimatedIcon and it's only 59 lines of code,  shouldn't be difficult to understand, if something isn't clear (or you have problems customizing it to your needs or integrating it)  you  should just ask (but google first).

---

### Post by Nytram on 2010-12-12
> **t1497f35 said:**
> The class that matters is AnimatedIcon and it's only 59 lines of code,  shouldn't be difficult to understand, if something isn't clear (or you have problems customizing it to your needs or integrating it)  you  should just ask (but google first).

Look I've said this twice already but I'll say it again - I'm new to Java. As in, it's my very first program, Ok?

I'm sure it is simple code for you, but not for a beginner like me. Tell me, how many years of Java do you have under your belt?

Sure I probably could understand your code if I spent hours Googling it, but why bother? Static images will do just fine.

---

### Post by t1497f35 on 2010-12-12
That is true unless Java is your first programming lang.
For how long am I using Java? - I'm not sure, about 1 year I guess.
Ok, no bad blood dude, I'm suggesting not compelling :)

---

### Post by StrayEddy on 2012-02-13
Here, It's simple and works:

Image image =Toolkit.getDefaultToolkit().createImage("path to my image");
ImageIcon xIcon = new ImageIcon(image);
xIcon.setImageObserver(this);

---

