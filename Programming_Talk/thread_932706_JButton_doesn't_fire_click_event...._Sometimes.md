---
title: "JButton doesn't fire click event.... Sometimes"
date: 2008-09-28
forum: Programming Talk
---

### Post by doas777 on 2008-09-28
Howdy all,

I have a JButton in my java 6 application that does not register click events about 20% of the time. The button border highlights and the "push down/up" animation renders (so Swing recognizes the click), but the event handler just does not fire. I've read a few suspicions online, that the exact area of the button clicked could be dead.

The form that this button is on is dynamic and changes every few seconds. when other parts of the screen rerender the button calculates it's new size and redraws itself. I have a sneaking suspicion that this may be the cause, but I have no real evidence to back that up.

I really need to find a fix for this one. any ideas?

Thanks,
Franklin

---

### Post by drubin on 2008-09-28
Post the out put of 
```

java --version
javac --version
```

Also could you please give us a small demo version of your code so we can see if it is your code or the current configuration on your system.

---

### Post by doas777 on 2008-09-28
I switched to using mouse_press instead of mouse_clicked and it seems to help at least a little.

my java -version is:
```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

and javac -version is 
```

javac 1.6.0_07

```

here are some selected exceprts from my form:
```


btnMain.addMouseListener(new java.awt.event.MouseAdapter() {
    public void mousePressed(java.awt.event.MouseEvent evt) {
                btnMainMouseClicked(evt);
    }
});

private void btnMainMouseClicked(java.awt.event.MouseEvent evt) {                                     
   this.mainClicked(); 
}                                    


public void mainClicked(){
   if( this._AlreadySuspicious) {
        this._ostracizer.KeyInputRecieved(global.MainPrompt2(), new Date());
        this.stop();
        System.exit(0);
    }else{
      this._ostracizer.KeyInputRecieved(global.MainPrompt1(), new Date());
      this.btnMain.setText(global.MainPrompt2());
      this._AlreadySuspicious = true;
    }
}  

public void drawMainButton(){
     try{
            Rectangle loc =  this.calcMainBtnLocation();
            //this.btnMain.setBounds(loc);
            this.DebugButtonPostionAndSize(btnMain, "drawMainButton()");
            this.btnMain.setFont( new java.awt.Font(
                         this.btnMain.getFont().getName(), 
                         this.btnMain.getFont().getStyle(), 
                         (int)(loc.getHeight() - (loc.getHeight() * 0.30))));
            this.btnMain.setPreferredSize(loc.getSize());
            this.btnMain.setMinimumSize(loc.getSize());
            this.btnMain.repaint(this.btnMain.getBounds());
            this.DebugButtonPostionAndSize(btnMain, "drawMainButton()");
       }catch(Exception e){
            global.raiseErr(e, "frmMain.drawMainButton()");
       }
}

 private Rectangle calcMainBtnLocation(){
      try{
            int AR = 20; //20w:1h
            int hpad = 80; //padding from the bottom of the left image
            int x = (int)this.btnLeft.getLocation().getX();
            int y = (int)(this.btnLeft.getLocation().getY() 
                                             + this.btnLeft.getHeight() + hpad);
            int w = (int)(this.btnLeft.getWidth() + this.btnRight.getWidth() + 20);
            int h = w / AR;
            return new Rectangle(x,y,w,h);
      }catch(Exception e){
            global.raiseErr(e, "frmMain.calcMainBtnLocation()");
      }
      return null;
}


```

I've attached the whole form as well. it's a netbeans project so I included the .form .

thanks,
Franklin

---

### Post by doas777 on 2008-09-30
bump

---

