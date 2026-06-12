---
title: "Java awt question (JScrollPane and JTextArea)"
date: 2009-05-27
forum: Programming Talk
---

### Post by Kralizec on 2009-05-27
Before I begin, let me say that my problem is *not* regarding how to put a JTextArea in a JScrollPane. I've already done that and it works fine.
My problem is that now that I've put my text area in the scroll pane, I can no longer access/modify the text in the text area. getText() always returns an empty string, the document returned by getDocument() is also empty, and I cannot modify the text using setText().
Any suggestions would be greatly appreciated.

---

### Post by mike_g on 2009-05-27
Maybe you could post the code? 

I did a very quick mockup in netbeans which works for me:
```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Window extends JFrame {
       public Window(){
           this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
           JPanel content = new JPanel();
           final JTextArea ta = new JTextArea();
           ta.setPreferredSize(new Dimension(200, 40));
           JScrollPane sp = new JScrollPane(ta);
           JButton btn = new JButton("Hit me!");
           btn.addActionListener(new ActionListener() {
               public void actionPerformed(ActionEvent e) {
                   System.out.println(ta.getText());
               }
           });
           content.add(sp); 
           content.add(btn);
           this.add(content);
           this.setVisible(true);
           this.pack();
       }
}
```

---

### Post by Kralizec on 2009-05-27
Thank you for your reply.

Here is a code segment containing the relevant code:
```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

//class definition, etc. here

private static JTextArea commBox;

//other code (initializing other instance variables)

commBox = new JTextArea(5, 15);
JScrollPane scroll = new JScrollPane(commBox);
commBox.setLineWrap(true);
commBox.setWrapStyleWord(true);

//Other code

//The relevant action listener
JButton submit = new JButton("Submit Entry");
    submit.setMnemonic(KeyEvent.VK_ENTER);
    submit.addActionListener(
        new ActionListener()
	{
	    public void actionPerformed(ActionEvent e)
	    {
	        try {
		    if(SQL.add(con, getDate(), getMaintenance(), getComments()) == 1)
		    JOptionPane.showMessageDialog(frame, "Entry successfully added.");
		} catch (SQLException sqle)
		{
		    JOptionPane.showMessageDialog(frame, "Uh-oh, entry unsuccessful.");
		}
	    }
	});

//other code

//The helper method
public String getComments()
    {
        System.out.println(commBox.getText());
	return commBox.getText();
    }

```

I've also attached the whole .java file as .txt in case having the entire code body would be helpful.

---

### Post by pbrockway2 on 2009-05-27
From the code that you attached:

```
commBox = new JTextArea(5, 15);
JScrollPane scroll = new JScrollPane(commBox);
commBox.setLineWrap(true);
commBox.setWrapStyleWord(true);
commLabel.setLabelFor(commBox);
commBox = new JTextArea(5, 15);
```

As you can see you put *commBox* into *scroll* but then you set the value of the (static) *commBox* to something else.  It's the text area in the scroll pane that gets added ultimately to the frame, but it's the other one that you later look at to getText().

Constructing a [SSCCE]("http://sscce.org/") is always good. (rather than picking out from the code what you imagine might be important, or posting the whole thing.)  I say this not to be picky, but because in this instance it would have revealed the problem (basically just a typo - some code remaining from what you had before you decided to use the scroll pane.)

---

### Post by Kralizec on 2009-05-27
How about that...I completely missed that line. Thank you very much. I'll look into the SSCCE for the next time I post code.

---

### Post by pbrockway2 on 2009-05-27
> **Kralizec said:**
> How about that...I completely missed that line. Thank you very much. I'll look into the SSCCE for the next time I post code.

You're welcome.  The internet means you always have another pair of eyes!

---

