---
title: "Java: Make a change before the end of the method"
date: 2011-02-20
forum: Programming Talk
---

### Post by Eredeath on 2011-02-20
Please excuse me if my terminology is incorrect. I'm a beginner at Java and learning it on my own. I'm trying to create an interval timer where once the timer is started the window will turn yellow for five seconds, then green for a user set time and red for a user set time. Here is my class int_timer:
```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
/**
 * 
 * @author Eredeath
 * @version .01b
 */
public class int_timer implements ActionListener
{   
    private static String[] INPUTS = new String[3];
    private String TIMEON = "2";
    private String TIMEOFF = "2";
    private String ROUNDS = "2";
    private JTextField  TonIn, ToffIn, round;
    public Container intScreen;
    
    public void screen(Container ContentPane) {
        
        JLabel TonPrompt, ToffPrompt, roundPrompt;
        JButton     startButton;
        
        intScreen = ContentPane; 
        intScreen.removeAll();
        intScreen.repaint();
        
        JPanel      okayPanel, InPanel;
        intScreen.setLayout(new BorderLayout());
        
        //Text Field inputs
        InPanel = new JPanel(new GridLayout(0,1));
        //input for Time on
        TonPrompt = new JLabel();
        TonPrompt.setText("Enter Time on in seconds: ");
        TonPrompt.setSize(150,5);
        InPanel.add(TonPrompt);

        TonIn = new JTextField(TIMEON);
        TonIn.setColumns(5);
        InPanel.add(TonIn);
        //TonIn.addActionListener(this);
        
       //input for Time off
        ToffPrompt = new JLabel();
        ToffPrompt.setText("Enter Time off in seconds: ");
        ToffPrompt.setSize(150,5);
        InPanel.add(ToffPrompt);

        ToffIn = new JTextField(TIMEOFF);
        ToffIn.setColumns(5);
        InPanel.add(ToffIn);
        //TonIn.addActionListener(this);
      
        //input for Rounds
        roundPrompt = new JLabel();
        roundPrompt.setText("Enter number of rounds: ");
        roundPrompt.setSize(150,5);
        InPanel.add(roundPrompt);
        
        round = new JTextField(ROUNDS);
        round.setColumns(1);
        InPanel.add(round);
        //TonIn.addActionListener(this);

        intScreen.add(InPanel, BorderLayout.CENTER);

        //create okay button
        okayPanel = new JPanel(new FlowLayout());
        startButton = new JButton("Start!");
        startButton.setSize(30, 30);
        okayPanel.add(startButton);
        intScreen.add(okayPanel, BorderLayout.SOUTH);
        intScreen.validate();
        
        //action listener for start button
        startButton.addActionListener(this);       
    }

    public void actionPerformed(ActionEvent event) {
        //string array
        INPUTS[0] = TonIn.getText();
        INPUTS[1] = ToffIn.getText();
        INPUTS[2] = round.getText();
        if (validateInputs(INPUTS)){
            RunIntTimer(INPUTS);
        }
    }
    
    public boolean validateInputs(String[] inputs){
        for (int i = 0; i < inputs.length; i++) {
            try{
                Integer.parseInt(inputs[i]);
            }
            catch (NumberFormatException e){
                JOptionPane.showMessageDialog(null, "please enter digits only.");
                return false;
            }
        }
        return true;
    }
    public int[] inputsToInts(String[] inputs){
        int[] intin = new int[inputs.length];
        for (int i = 0; i < inputs.length; i++){
            intin[i] = Integer.parseInt(inputs[i]);
        }
        return intin;
    }
    
    [COLOR="DarkGreen"]public void RunIntTimer(String[] inputs){
        
        //get the times and rounds and convert them to integers
        int[] timeRnds = new int[inputs.length];
        timeRnds = inputsToInts(inputs);
        int timeon  = timeRnds[0];
        int timeoff = timeRnds[1];
        int rounds   = timeRnds[2];
        
        //clear the container
        //intScreen = ContentPane; 
        
        intScreen.removeAll();
        intScreen.repaint();
        
        int rnds = rounds; //dummy variable for rounds
        do {
            if (rounds == rnds){
                bgYellow();
                fiveSecWait();
            }
            bgGreen();
            Timer(timeon);
            bgRed();
            Timer(timeoff);
            rounds--;
        } while (rounds > 0);
    }[/COLOR]
    
    private void fiveSecWait(){
        long fiveSecWait = System.currentTimeMillis();
        while (fiveSecWait > (System.currentTimeMillis() - 5000)){
        }
    }
    
    private void Timer(int time){
        long timenow = System.currentTimeMillis();
        while (timenow > (System.currentTimeMillis() - (time * 1000))){
        }
    }
        
    private void bgYellow(){
        //Container contentPane = getContentPane( );
        intScreen.setBackground(Color.YELLOW);
    }
    private void bgGreen(){
        //Container contentPane = getContentPane( );
        intScreen.setBackground(Color.GREEN);
    }
    private void bgRed(){
        //Container contentPane = getContentPane( );
        intScreen.setBackground(Color.RED);
    }
}
```
The portion I'm having the difficulty with is my RunIntTimer method. Instead of clearing the container and coloring the background yellow for 5 seconds then green then red it will look like it froze then after 13 seconds turn red.
How do I get it to change before the end of the method?

---

### Post by Eredeath on 2011-02-20
In researching this I found that my method for timing isn't the best. Watching my CPU usage while running this program, I found it hitting 100%
If someone wants to weight in on that too, it would be much apprciated.
But I'm heading to bed for the evening. I guess I'll try again tomorrow.

---

### Post by NovaAesa on 2011-02-20
What you are currently doing is called "busy waiting". In almost all circumstances, this is a bad idea:
```

time t = now
while t < now + 5 {
  //do nothing
}

```

Java has pretty good thread management built into the language. Have a look here at the Thread class's sleep method. [http://download.oracle.com/javase/6/docs/api/java/lang/Thread.html#sleep(long](http://download.oracle.com/javase/6/docs/api/java/lang/Thread.html#sleep(long))

So if you wanted to "pause" execution for 5 seconds, you would use the code:
```

Thread.sleep(5000);

```

---

### Post by Eredeath on 2011-02-20
> **NovaAesa said:**
> What you are currently doing is called "busy waiting". In almost all circumstances, this is a bad idea:
```

time t = now
while t < now + 5 {
  //do nothing
}

```

Java has pretty good thread management built into the language. Have a look here at the Thread class's sleep method. [http://download.oracle.com/javase/6/docs/api/java/lang/Thread.html#sleep(long](http://download.oracle.com/javase/6/docs/api/java/lang/Thread.html#sleep(long))

So if you wanted to "pause" execution for 5 seconds, you would use the code:
```

Thread.sleep(5000);

```

During that wait period I was hoping to be executing more code. I wanted to later on put in a count down UI as well. From the sounds of it, the sleep method won't allow me to do that.

---

### Post by Zugzwang on 2011-02-20
> **Eredeath said:**
> During that wait period I was hoping to be executing more code. I wanted to later on put in a count down UI as well. From the sounds of it, the sleep method won't allow me to do that.

Ah, ok, I think that it's clear now what you want.

Whenever you do computations that do some time, the Java Swing environment forces you to move them to a different thread. UI elements are only updated if the UI thread is not used at the moment. Thus, whenever some action listener is called, changes to the UI do not take effect until you return from it. Thus, you need to make longer-taking computations from a different thread in order to avoid freezing of the GUI.

At the same time, UI elements are only updated by the UI thread. Thus, in order to do something like you want to do, spawn a computation thread and inject change requests to the UI into the UI-Thread's toDo list by using invokeLater.

Some links for further reading:
[http://java.sun.com/products/jfc/tsc/articles/threads/threads1.html](http://java.sun.com/products/jfc/tsc/articles/threads/threads1.html)
[http://download.oracle.com/javase/tutorial/uiswing/concurrency/initial.html](http://download.oracle.com/javase/tutorial/uiswing/concurrency/initial.html)

---

### Post by Eredeath on 2011-02-20
Wow... that's much more complicated than I had originally thought it would be. I will read through the links you sent and see where that takes me. 
Thank you.

---

