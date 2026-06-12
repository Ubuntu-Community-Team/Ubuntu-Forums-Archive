---
title: "[Java] How can I flash a message within a JTextField?"
date: 2011-06-03
forum: Programming Talk
---

### Post by dwhitney67 on 2011-06-03
I'm developing a trivial Java application which utilizes a JTextField.  Within this text field, I want to display a message, and then moments later, I want to replace the message with another message.

I tried something like this, but it does not work (the first message is never displayed):
```

textfield.setText(msg1);

try {
   Thread.sleep(2000);   // delay 2 seconds
}
catch (InterruptedException e) {}

textfield.setText(msg2);

```

Any suggestions?

---

### Post by PaulM1985 on 2011-06-03
I think you need to call "repaint()" before your sleep.

Paul

EDIT: A quick, hacky example.  (Note you will have to force this to quit, closing the window won't work)

```

import javax.swing.*;

class test extends JFrame
{

	public static void main(String[] args)
	{
		test t = new test();
		t.run();
	}

	private JTextField textfield;
	public test()
	{
		super();
		setSize(300, 300);
		textfield = new JTextField("Hello1");
		add(textfield);	
		setVisible(true);
	}

	public void run()
	{
		int i = 0;
		while (true)
		{
			if (i % 2 == 0)
			{
				textfield.setText("Hello");
			}
			else
			{
				textfield.setText("Hello2");
			}

			repaint();

			try
			{
				Thread.sleep(2000);
			}
			catch (Exception e)
			{
			}
			i++;
		}
	}
}

```

---

### Post by dwhitney67 on 2011-06-03
> **PaulM1985 said:**
> I think you need to call "repaint()" before your sleep.


Thanks Paul, but the call to repaint() doesn't work.  Your example did not properly implement the requirement I was seeking.  Here's a spin on your test program to demonstrate that the repaint() does not work.
```

import javax.swing.*;

class test extends JFrame
{
        public static void main(String[] args)
        {
                test t = new test();
                t.run();
        }

        private JTextField textfield;
        public test()
        {
                super();
                setSize(300, 300);
                textfield = new JTextField();
                add(textfield);
                setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                setVisible(true);
        }

        public void run()
        {
                textfield.setText("Hello");

                repaint();

                // At this point, I want to see "Hello"... but I do not.

                delay(2000);

                textfield.setText("Goodbye");
        }

        private void delay(int millis)
        {
                try {
                        Thread.sleep(2000);
                }
                catch (Exception e) {}
        }
}

```

P.S.  I am going to experiment with the usage of a Timer.

---

### Post by Zugzwang on 2011-06-03
I think that your problem is that you execute your delay() in the GUI event dispatching thread, and nothing is painted until your are not executing one of your functions anymore and control is given back to the event dispatcher. The solution is to use a second thread for waiting. Note that painting must only occur in the event dispatching thread, and thus, you will need to inject a call to your repainting business. The following example is a quite ugly one for doing so, obtained by modifying your code.

```

import javax.swing.*;

class test extends JFrame
{
        public static void main(String[] args)
        {
                test t = new test();
                t.run();
        }

        private JTextField textfield;
        public test()
        {
                super();
                setSize(300, 300);
                textfield = new JTextField();
                add(textfield);
                setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                setVisible(true);
        }

        public void run()
        {
                textfield.setText("Hello");

                repaint();

                // At this point, I want to see "Hello"... but I do not.
                
                (new Thread() {
                    public void run() {
                        delay(2000);

                        SwingUtilities.invokeLater(new Runnable() {
                            public void run() {
                                textfield.setText("Goodbye");
                            }
                        });
                    }
                }).start();
        }

        private void delay(int millis)
        {
                try {
                        Thread.sleep(2000);
                }
                catch (Exception e) {}
        }
}

```

It appears as if the following reference contains more information: [http://book.javanb.com/jfc-swing-tutorial-the-a-guide-to-constructing-guis-2nd/ch09lev1sec9.html](http://book.javanb.com/jfc-swing-tutorial-the-a-guide-to-constructing-guis-2nd/ch09lev1sec9.html)

EDIT: I don't think that calling "repaint" is actually necessary in your example, as calling setText on a Label or TextField should trigger this automatically.

---

### Post by PaulM1985 on 2011-06-03
> **dwhitney67 said:**
> Thanks Paul, but the call to repaint() doesn't work.  Your example did not properly implement the requirement I was seeking.  Here's a spin on your test program to demonstrate that the repaint() does not work.

That's interesting.  I ran the code I sent you and it worked on my PC.  I also ran the code that you sent and got both "Hello" and "Goodbye".

I actually thought that the sleep in this thread would have given control back to the event dispatcher and allowed a repaint.  Maybe this is an issue relating to the JVM that is running the program.

Sorry it didn't work in your case, I only sent it because it worked on my PC.

Paul

---

### Post by t1497f35 on 2011-06-03
[PHP]
package test;

import java.awt.BorderLayout;
import javax.swing.*;

public class Main extends JFrame {

    public static void main(String args[]) {
        new Main();
    }
    
    public Main() {
        TField tfield = new TField("Message #1", "Message #2");
        getContentPane().add(BorderLayout.NORTH, tfield);
        tfield.launchDelayedMessage(3000);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setSize(500, 500);
        setVisible(true);
    }
}

class TField extends JTextField implements Runnable {

    String s1, s2;
    int sleep;

    public TField(String s1, String s2) {
        this.s1 = s1;
        this.s2 = s2;
        setText(s1);
    }

    public void launchDelayedMessage(int millisec) {
        sleep = millisec;
        Thread th = new Thread(this);
        th.start();
    }

    @Override
    public void run() {
        try {
            Thread.sleep(sleep);
        } catch (Exception exc) {
        }
        setText(getText().equals(s1) ? s2 : s1);
    }
}
[/PHP]

---

### Post by dwhitney67 on 2011-06-03
I ended up utilizing the TimerTask class and a Timer.  This is my first stab at developing a Java program in years, so if there is anyway to simplify the program, please let me know.

```

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.util.Timer;
import java.util.TimerTask;

public class MathCalc extends JFrame
{
   public static void main(String[] args)
   {
      MathCalc mc = new MathCalc();
      mc.generateProblem();
      mc.setVisible(true);
   }


   private static int ASK_SAME_QUESTION = 0;
   private static int ASK_NEW_QUESTION  = 1;

   private static int DIFF_EASY_FACTOR   = 10;
   private static int DIFF_MEDIUM_FACTOR = 50;
   private static int DIFF_HARD_FACTOR   = 100;

   private JTextField     textArea;
   private String         question;
   private int            result;
   private int            difficultyFactor;
   private int            nextAction;
   private Timer          timer = new Timer();
   private ScheduleRunner scheduleRunner;

   public MathCalc()
   {
      difficultyFactor = DIFF_EASY_FACTOR;
      nextAction = ASK_NEW_QUESTION;

      // Setup menu
      JMenuBar             menubar = new JMenuBar();
      JMenu                file    = new JMenu("File");
      JMenu                help    = new JMenu("Help");
      JMenuItem            newcalc = new JMenuItem("Generate New Problem");
      JMenu                diff    = new JMenu("Set Difficulty");
      JRadioButtonMenuItem easy    = new JRadioButtonMenuItem("Easy");
      JRadioButtonMenuItem medium  = new JRadioButtonMenuItem("Medium");
      JRadioButtonMenuItem hard    = new JRadioButtonMenuItem("Hard");
      JMenuItem            exit    = new JMenuItem("Exit");
      JMenuItem            howto   = new JMenuItem("How to Play");
      JMenuItem            about   = new JMenuItem("About Math Calculator");

      ButtonGroup btg = new ButtonGroup();
      btg.add(easy);
      btg.add(medium);
      btg.add(hard);
      easy.setSelected(true);

      diff.add(easy);
      diff.add(medium);
      diff.add(hard);

      file.add(newcalc);
      file.add(diff);
      file.addSeparator();
      file.add(exit);

      help.add(howto);
      help.add(about);

      menubar.add(file);
      menubar.add(help);

      setJMenuBar(menubar);

      // Setup text field
      textArea = new JTextField();
      textArea.setEditable(false);

      // Setup numeric keypad
      JPanel keypad = new JPanel();
      keypad.setLayout(new GridLayout(4, 3));

      JButton btn;

      for (int i = 6; i >= 0; i -= 3)
      {
         for (int j = 1; j <= 3; ++j)
         {
            btn = new JButton("" + (j + i));

            keypad.add(btn);

            final int btnNum = j + i;
            btn.addActionListener(new ActionListener() {
                                      public void actionPerformed(ActionEvent e) {
                                         processKeypadInput(btnNum);
                                      } } );
         }
      }
      btn = new JButton("" + 0);
      keypad.add(btn);
      btn.addActionListener(new ActionListener() {
                                   public void actionPerformed(ActionEvent e) {
                                      processKeypadInput(0);
                                   } } );

      btn = new JButton("Clear");
      keypad.add(btn);
      btn.addActionListener(new ActionListener() {
                                   public void actionPerformed(ActionEvent e) {
                                      clearKeypadInput();
                                   } } );

      btn = new JButton("Enter");
      keypad.add(btn);
      btn.addActionListener(new ActionListener() {
                                   public void actionPerformed(ActionEvent e) {
                                      checkKeypadInput();
                                   } } );

      // Insert keypad and text field into their own panel
      JPanel calc = new JPanel(new BorderLayout());
      calc.add(textArea, BorderLayout.NORTH);
      calc.add(keypad, BorderLayout.CENTER);

      add(calc);

      // Set other attributes
      setTitle("Math Calculator");
      setSize(250, 150);
      setLocationRelativeTo(null);
      setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

      // Setup menu action listeners
      newcalc.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    generateProblem();
                                 } } );
      easy.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    setDifficulty(DIFF_EASY_FACTOR);
                                 } } );
      medium.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    setDifficulty(DIFF_MEDIUM_FACTOR);
                                 } } );
      hard.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    setDifficulty(DIFF_HARD_FACTOR);
                                 } } );
      exit.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    System.exit(0);
                                 } } );
      howto.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    showHowto();
                                 } } );
      about.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    showAbout();
                                 } } );
   }

   public void generateProblem()
   {
      String operation = ((int)(Math.random() * 10) % 2 == 1 ? " + " : " - ");

      int val1 = (int)(Math.random() * difficultyFactor);
      int val2 = (int)(Math.random() * difficultyFactor);

      if (val2 > val1)
      {
         int tmp = val1;
         val1 = val2;
         val2 = tmp;
      }

      question = "" + val1 + operation + val2 + " = ";
      displayMessage(question);

      if (operation == " + ")
      {
         result = val1 + val2;
      }
      else
      {
         result = val1 - val2;
      }
   }

   private void setDifficulty(int diffFactor)
   {
      difficultyFactor = diffFactor;
      generateProblem();
   }

   private void processKeypadInput(int num)
   {
      displayMessage(getMessage() + num);
   }

   private void clearKeypadInput()
   {
      question.substring(0, question.indexOf('=') + 2); // keep whitespace after =
      displayMessage(question);
   }

   private void checkKeypadInput()
   {
      String text = getMessage();

      if (text.length() > question.length())
      {
         int answer = Integer.parseInt(text.substring(text.indexOf('=') + 2));

         if (answer == result)
         {
            displayMessage("That is correct!");
            nextAction = ASK_NEW_QUESTION;
            delay(2000);
         }
         else
         {
            displayMessage("Sorry, that is wrong; try again...");
            nextAction = ASK_SAME_QUESTION;
            delay(2000);
         }
      }
      else
      {
         displayMessage("Input your answer!");
         nextAction = ASK_SAME_QUESTION;
         delay(2000);
      }
   }

   private void displayMessage(String msg)
   {
      textArea.setText(msg);
   }

   private String getMessage()
   {
      return textArea.getText();
   }

   private int getAction()
   {
      return nextAction;
   }

   private void showHowto()
   {
      // TODO
   }

   private void showAbout()
   {
      // TODO
   }

   private void delay(int delayInMillis)
   {
      scheduleRunner = new ScheduleRunner(this);
      timer.schedule(scheduleRunner, delayInMillis);
   }

   private class ScheduleRunner extends TimerTask
   {
      private MathCalc mathCalc;

      public ScheduleRunner(MathCalc mathCalc)
      {
         this.mathCalc = mathCalc;
      }

      public void run()
      {
         if (mathCalc.getAction() == MathCalc.ASK_SAME_QUESTION)
         {
            mathCalc.clearKeypadInput();
         }
         else
         {
            mathCalc.generateProblem();
         }
      }
   }
}

```

---

### Post by t1497f35 on 2011-06-03
You just posted your complete app, ain't you afraid somebody's gonna take it and sell it on the black market?

---

### Post by Reiger on 2011-06-03
Your code creating and accessing the GUI components is not guaranteed to run on the Event Dispatch (GUI) Thread. Typical way to ensure this:

```

java.awt.EventQueue.invokeLater(new Runnable() {
    
    @Override
    public void run() {
      // your code here.
      // it is guaranteed to execute on the GUI thread
    }
});

``` Specifically the scheduled tasks will run in the timer thread.

IIRC Timer exposes a schedule method to run a single TimerTask repeatedly, which seems to fit your app logic better. Might want to look into that.

---

### Post by dwhitney67 on 2011-06-04
> **t1497f35 said:**
> You just posted your complete app, ain't you afraid somebody's gonna take it and sell it on the black market?

It would be awesome if someone would steal it and make money off of it; then I could sue them.

But seriously, why would anyone want to copy a simple app such as the one I posted?  I developed it for my 6 year old daughter so she could practice her math skills.  As she gets older, I will add other operations such as multiplication, division, floating point capabilities, etc.

---

