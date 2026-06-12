---
title: "password fields in java applets"
date: 2011-09-16
forum: Programming Talk
---

### Post by vineeth v s on 2011-09-16
hi,

does anyone know how to get a password field of stars using applets?

i already created with jpasswordfield in java swing but can't find anythings 
with applets.... any help??:popcorn:

---

### Post by PaulM1985 on 2011-09-16
Are you saying you can't use a JPasswordField in an Applet?  Are you using JApplets?  If so, you should just be able to add it like any other swing control.

Paul

---

### Post by amingv on 2011-09-16
I'm not sure I understand what you mean... do you want to change the character displayed when someone types a password in the applet to a star (*)?

Something like this?

[PHP]
import javax.swing.*;
import java.applet.*;

public class Test extends Applet
{
    private JLabel passwordLabel;
    private JPasswordField passwordField;
    
    public void init()
    {
        passwordLabel = new JLabel("Password: ");

        passwordField = new JPasswordField(10);
        passwordField.setEchoChar('*');
        
        add(passwordLabel);
        add(passwordField);
    }
}
[/PHP]

If that's not it, then please explain in more detail.

---

