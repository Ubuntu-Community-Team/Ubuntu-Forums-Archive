---
title: "ButtonListener and TextFieldListeners."
date: 2010-12-08
forum: Programming Talk
---

### Post by badbaby_87 on 2010-12-08
Hi. I'm writing a Java program that creates a multiplication quiz.  The factors are displayed, and the user enters their answer in the text field provided.  They then click on the "Check Answers" button, which will identify which problems are incorrect.  

My problem is that nothing happens when I click the Check Answers button.  I set it up to where the entire background should change to red (I want individual incorrect cells to be changed, but one step at a time).  Nothing happens when I enter data and click the button.  What would help my code work the way I want? 

Thanks in advance![PHP]
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.*;
import java.util.List;
import java.lang.Object.*;





public class MultiplicationTable extends JFrame{

    int A = 0;
    int B = 0;

    /*Button for verifying Answer:*/
    private JButton jbtSubmit = new JButton("Check Answers");
    
        Scanner scanner = new Scanner(System.in);
        Random generator = new Random();


        /* arrays to store player's answer, the multiplication factors
         * and the solutions.
         */

        List answers = new ArrayList();
        int[] playerAnswer = new int[25];
        String[] multiFactors = new String[25];
        int[] multiFactorsSolns = new int[25];

//Constructor for a grid
public MultiplicationTable() {
        JFrame frame = new JFrame();
        frame.setTitle("Multiplication Quiz");

        //frame.addComponents;
        frame.setLayout(new BorderLayout());

        //fill factors array and obtain solutions:
        for(int k = 0; k < multiFactors.length; k++){
        int integerA = generator.nextInt(13);
        int integerB = generator.nextInt(13);

        multiFactors[k] = integerA + "X" +  integerB;
        multiFactorsSolns[k] = integerA * integerB;
        }

        /*instantiate jtf*/
        JPanel p1 = new JPanel(new GridLayout(5,5));
        for(int i = 0; i < multiFactors.length ; i++){

            JLabel factor = new JLabel(multiFactors[i]);
            JTextField jtf = new JTextField(3);

            p1.add(factor);
            p1.add(jtf);

            answers.add(jtf);
            jtf.addActionListener(new TextFieldListener());
        
        }
       

        p1.setVisible(true);

        JPanel p2 = new JPanel();
        p2.add(jbtSubmit);
         //button listener:
         jbtSubmit.addActionListener(new ButtonListener());

        frame.add(p1, BorderLayout.CENTER);
        frame.add(p2, BorderLayout.SOUTH);
        frame.setVisible(true);





}  //end MultiplicationTable()

     /* Handle button action*/
private class ButtonListener implements ActionListener {
    public void actionPerformed(ActionEvent e) {
  
    //verify answers:

        for(int p = 0; p < playerAnswer.length; p++){
        if(playerAnswer[p] == multiFactorsSolns[p]){
        setBackground(Color.BLUE);
        }
        else{
        setBackground(Color.red);
        }



        }

}}// end class ButtonListener

private class TextFieldListener implements ActionListener {
    public void actionPerformed(ActionEvent e) {
       
            for(int n =0; n < 25; n++){
                JTextField f = (JTextField)answers.get(n);
                playerAnswer[n] = Integer.parseInt(f.getText());
             }
             
        }
    }




 public static void main(String[] args){


        //construct a new object:
        MultiplicationTable myTable= new MultiplicationTable();


        myTable.setTitle("Multiplication Quiz");
        myTable.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myTable.pack();

    }//end main

 } //end class multiplication table



[/PHP]

---

### Post by r-senior on 2010-12-08
OK, a few suggestions to move forward:

1. Try putting System.out.println(...) statements in your listeners to check that they are being called correctly. Or use a debugger of course.

2. Do the same inside the if ... then ... else to check that correct answers are being assessed correctly.

3. Add a frame.setSize() to the constructor so the window is a sensible size

4. Consider what will happen if a field is left empty. Will it report a correct answer, an incorrect answer or throw an exception?

---

### Post by PaulM1985 on 2010-12-08
You are calling setBackground on the JFrame rather than setBackground on each of the text fields.  

Also, I think you want to be using aString.Equals(someString) when comparing strings because I am pretty sure that == will compare references to string objects, not actual strings.

Paul

---

### Post by badbaby_87 on 2010-12-08
Thanks for the tips!  I'll post back if I have any success.

---

