---
title: "JavaFX for Ubuntu Linux officially released"
date: 2009-06-03
forum: Programming Talk
---

### Post by froggyswamp on 2009-06-03
[http://javafx.com/docs/articles/javafx1-2.jsp](http://javafx.com/docs/articles/javafx1-2.jsp)

> 
Support    is now provided for two additional OS platforms: [IMG]http://javafx.com/docs/articles/add.png[/IMG]
    
    
[LIST]
[*]Solaris Beta: OpenSolaris 2009.06
[*]Linux Beta: Ubuntu 8.04 LTE
[/LIST]

Works on my 9.04 too.

---

### Post by Raaj on 2009-06-24
> **froggyswamp said:**
> [http://javafx.com/docs/articles/javafx1-2.jsp](http://javafx.com/docs/articles/javafx1-2.jsp)


Works on my 9.04 too.

I am having problems with key events. My javafx application works perfectly well on windows but on ubuntu 9.04, it is unresponsive to key events! I initially thought there might be a variation in the virtual key codes (VK_A .. etc) and to confirm it, I added the following snippet: 

```
    var bg = ImageView {
        onKeyTyped: function( e: KeyEvent ):Void {
            println("some key pressed");
            if(e.code==KeyCode.VK_A){
                println("key A pressed");
            }

        }

        onMouseClicked: function( e: MouseEvent ):Void {
            println("mouse clicked");
            fire();
        }
        

        image: Image {
            url: "{__DIR__}resources/bg.jpg"
        }
    };
```

But I was surprised to find that even "some key pressed" is not printed when any key is pressed. However, the MouseEvent works perfectly well.. HELP ...

---

### Post by Raaj on 2009-06-24
oh k .. the problem is solved ... the requestfocus() function has to be called in order to make the key events work. Guess this is a change in the 1.2 sdk .. and has nothing to do with ubuntu as I had presumed .. :)

---

### Post by jespdj on 2009-06-24
It works on my 64-bit Ubuntu 9.04, but I got a few small problems, so I filed a bug report. A few days ago one of the developers commented that 64-bit Linux is not supported at the moment.

Stupid... it's not 1999 anymore, when 64-bit was something exotic.

---

