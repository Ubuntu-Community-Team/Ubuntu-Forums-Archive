---
title: "[SOLVED] Java:Swing, where is the gap between JFrame and A JComponent?"
date: 2008-06-20
forum: Programming Talk
---

### Post by fyplinux on 2008-06-20
I created a simple JFrame with only one JPanel added.

Reading the boundary, The width, height, x, y of JFrame is:
    300,600,0,0
The values of JPanel is:
    294,568,0,0

The JPanel, where the range of points (0,0)-> (293,567)could be painted.

It seems JFrame is fulfilled by the JPanel, but the boundary of JPanel is smaller than the JFrame's, which is only a few pixels.
So, where is these pixels gone?

Thanks.

---

### Post by xlinuks on 2008-06-20
The JFrame has borders that occopy a few pixels whose size depends on the current L&F.
You can somewhat control that (however I doubt you wanna go to that trouble) by using the setUndecorated( boolean flag ) method inherited from java.awtFrame:
```

public void setUndecorated(boolean undecorated)

    Disables or enables decorations for this frame. This method can only be called while the frame is not displayable.

    Parameters:
        undecorated - true if no frame decorations are to be enabled; false if frame decorations are to be enabled. 
    Throws:
        IllegalComponentStateException - if the frame is displayable.
    Since:
        1.4
    See Also:
        isUndecorated(), Component.isDisplayable(), JFrame.setDefaultLookAndFeelDecorated(boolean)



```

---

### Post by xlinuks on 2008-06-20
In other words if you wanna have a fixed size JPanel
1) set the size of the panel
2) add it to the frame
3) don't set the size of the frame but call "frame.pack()" for the frame to adjust it's size according the size that the components inside it need.
This way you'll have a jpanel of the exact size you wish.

---

### Post by fyplinux on 2008-06-20
Thank you, xlinuks. Would you be able to give me some links or reference about the decorations, as I found If setUndecorated(true), even the titles are not shown. what properties(like the title) is related to the decorations?

And I think decoration is not a part of the border, because there is no getBorder() method for JFrame.

---

### Post by xlinuks on 2008-06-20
You're welcome,
please let me know what exactly you're trying to accomplish.
If you setUndecorated to true, than you won't have borders, but you won't have titles either, besides you won't be able to resize the window anymore using the mouse. There is no way to get rid of the windows borders and keep the title.

On the other hand, as I suggested on the second reply, if it's all about having a JPanel of an exact size - it's very easy - see my second reply. If something isn't clear, let me know.

---

