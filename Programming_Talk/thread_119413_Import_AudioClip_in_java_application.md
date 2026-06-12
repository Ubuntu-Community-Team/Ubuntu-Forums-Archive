---
title: "Import AudioClip in java application"
date: 2006-01-19
forum: Programming Talk
---

### Post by healychan on 2006-01-19
Hello all,

Is it possible to import an audio clip into a stand-alone java application ??
To import an AudioClip, I need to use the getAudioClip() method which is a method of Applet class. This means the container itself must be an Applet object, is that true ??

This is the structure of my application:

1. A JFrame containing a JLabel
2. The JLabel contains an ImageIcon

I would like the application to produce a "ben" sound when MouseClicked event occur. Since the container of the ImageIcon object is a JLabel, I am not able to access the getAudioClip() method.

Thanks for any helps;)

---

### Post by mostwanted on 2006-01-20
[QUOTE=healychan]Since the container of the ImageIcon object is a JLabel, I am not able to access the getAudioClip() method.[/QUOTE]

Yes you are. You just create an Applet class and use its method instead. I haven't actually done Java in a very long time and I only did it briefly, but this worked for me (it's not the same method name you gave but what the heck):

```
// Class for playing sounds in Java
// Uses applet class' simple audio-playing capabilities

import java.net.URL;
import java.applet.*;

public class JavaSound {
    public void playFile(String file) {
        try {
            URL soundToPlay = getClass().getResource(file);
            AudioClip player = Applet.newAudioClip(soundToPlay);
            player.play();
        } catch (Exception e) {}
    }
}
```

And then you invoke it with

```

JavaSound player = new JavaSound();
player.playFile("/path/to/mySound.wav");
```

---

### Post by healychan on 2006-01-20
Thanks for your reply.

I read some tutorials on Sun.com. The codes are very similar to yours.
```
import java.applet.*;
import javax.swing.*;
import java.net.URL;
import java.net.MalformedURLException;

class SoundLoader extends Thread {
    SoundList soundList;
    URL completeURL;
    String relativeURL;

    public SoundLoader(SoundList soundList,
                       URL baseURL, String relativeURL) {
        this.soundList = soundList;
        try {
            completeURL = new URL(baseURL, relativeURL);
        } catch (MalformedURLException e){
            System.err.println(e.getMessage());
        }
        this.relativeURL = relativeURL;
        setPriority(MIN_PRIORITY);
        start();
    }

    public void run() {
        AudioClip audioClip = Applet.newAudioClip(completeURL);
        soundList.putClip(audioClip, relativeURL);
    }
}

```
The way they create an URL is different from yours. They call the constructor of URL( URL, String ) to create an URL object. 

Well, one thing I don't understand is the "file" variable.
For example, if my audio clip stores in "/home/admin/abc.au", the "file" variable should be "/home/admin/abc.au", right??

In the example provided by Sun, they need to specify the protocol when create an URL object. Therefore, if my file is in "/home/admin/abc.au", I need to pass "file:///home/admin/abc.au" to the constructor.

Thanks for your simple, newbie friendly example.:p

---

### Post by healychan on 2006-01-20
I am able to play audio clip now:p , thanks for your help.

Now I have an other question which is about Container objects.

I am going to make a JPanel that contains two JLabel, and one of the JLabel is on top of the other.  The JLabel at the front is smaller than the one at the back. Therefore, the audio clip will play when user click on the frontground JLabel but not the background JLabel.

I guess I can achieve the result by using absolute positioning instead of Layout Manager, am I correct ?? If not, what can I do ?? 

Again, thanks for any help.;)

---

### Post by Viro on 2006-01-21
Firstly, why on earth would you want to create a JLabel that sits on top of another JLable(effectively obscuring it?).  As far as I know, you can't add an ActionListener to the JLabel, and so you will have to manually handle mouse clicks yourself. Wouldn't it be better to use a JButton?

---

### Post by healychan on 2006-01-21
[QUOTE=Viro]Firstly, why on earth would you want to create a JLabel that sits on top of another JLable(effectively obscuring it?).  As far as I know, you can't add an ActionListener to the JLabel, and so you will have to manually handle mouse clicks yourself. Wouldn't it be better to use a JButton?[/QUOTE]
Since JLabel is a subclass of Component, it can access the method addMouseListener(). I don't need to handler mouse event myself.

The reason I use JLabel instead of JButton is because the content is an image. I would like the image displays as an image rather than a button.

---

### Post by Viro on 2006-01-23
If you're using mouselisteners, you need to handle the mouseclicks yourself. That's what MouseListener does. It tells you when a mouse was clicked, and what button was clicked, etc.

JButtons can use images too. I do not see the reason for trying to use JLabels. In any case, for if you want to position a component above one another, you can try absolute positioning. Just set the layout to null, and position your components.

---

### Post by healychan on 2006-01-23
Thank you so much from all of you. I am able to play sound and am able to put one JLabel on top of other JLabel using absoluate positioning.

I was searching for a tutorial about using absoluate positioning and here is the link. I hope people who have the same problem as me will found it useful. [http://java.sun.com/docs/books/tutorial/uiswing/layout/none.html]("http://java.sun.com/docs/books/tutorial/uiswing/layout/none.html")

Actually I am trying to make a simple shooting game. I will release a trial once I have my draft finished.

---

