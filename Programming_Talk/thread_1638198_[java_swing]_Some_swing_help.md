---
title: "[java swing] Some swing help?"
date: 2010-12-05
forum: Programming Talk
---

### Post by skytreader on 2010-12-05
I wonder why the sizes I specify for my JTextArea's don't reflect on the GUI. Also, I put myMessage in a JScrollPane---why isn't it working?

```
import javax.swing.BoxLayout;
import java.awt.Container;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextArea;
import javax.swing.JEditorPane;
import javax.swing.JPanel;
import javax.swing.JRootPane;
import javax.swing.JScrollPane;

public class GUIRunnable implements Runnable{
	public void run(){
		JFrame MainFrame = new MyFrame(500, 500);
		Container MainContainer = MainFrame.getContentPane();
		MainContainer.setLayout(new BoxLayout(MainContainer, BoxLayout.Y_AXIS));
		
		JTextArea myMessage = new JTextArea(4, 70);
		myMessage.setLineWrap(true);
		JScrollPane message = new JScrollPane(myMessage);
		JButton Send = new JButton("Send");
		JTextArea communications = new JTextArea(4, 70);
		JButton Connect = new JButton("Connect");
		JButton Disconnect = new JButton("Disconnect");
		Disconnect.setEnabled(false);
		
		JPanel ConnectionControlPanel = new JPanel();
		ConnectionControlPanel.setLayout(new BoxLayout(ConnectionControlPanel, BoxLayout.X_AXIS));
		ConnectionControlPanel.add(Connect);
		ConnectionControlPanel.add(Disconnect);
		
		MainContainer.add(myMessage);
		MainContainer.add(Send);
		MainContainer.add(communications);
		MainContainer.add(ConnectionControlPanel);
	}
}
```

And of course,

```
import java.awt.EventQueue;

public class GUIMain{
	public static void main(String[] args){
		EventQueue.invokeLater(new GUIRunnable());
	}
}
```

Any thoughts? Much thanks!

---

### Post by skytreader on 2010-12-05
My bad! I didn't add the JScrollPane to the Container. >.<

---

