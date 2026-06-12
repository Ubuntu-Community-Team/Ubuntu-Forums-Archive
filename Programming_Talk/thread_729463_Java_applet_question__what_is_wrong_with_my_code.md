---
title: "Java applet question : what is wrong with my code?"
date: 2008-03-19
forum: Programming Talk
---

### Post by AlexenderReez on 2008-03-19
this is my code --->

[PHP]import java.awt.*;

import java.applet.*;

import java.awt.event.*;

import javax.swing.*;





// Tells the applet you will be using the ActionListener methods.



public class GradeViewAssignment extends Applet implements ActionListener

{



     Button okButton;

     Button wrongButton;

     TextField nameField;

     private JButton red,blue, green, yellow, orange; // the JButtons which will cause the background colors to change

     

     





     public void init() 

     {

  // Now we will use the FlowLayout

          setLayout(new FlowLayout());

          okButton = new Button("Grade");

          nameField = new TextField("Type Your exam mark here",35);

          add(okButton);

          add(nameField);



  // Attach actions to the components

          okButton.addActionListener(this);

          }



 // Here we will show the results of our actions

         public void paint(Graphics g)

         {

  

double aDouble = Double.parseDouble(nameField.getText());



          if (aDouble >= 80 && aDouble <= 100)this.setBackground(Color.blue);



        if (aDouble >= 75&& aDouble < 80)this.setBackground(Color.green);



        if (aDouble >= 65 && aDouble < 75)this.setBackground(Color.yellow);

    

  // Now that the color is set you can get the text out the TextField

  // like this

          g.drawString(nameField.getText(),20,100);

     }



 // When the button is clicked this method will get automatically called

 // This is where you specify all actions.



        public void actionPerformed(ActionEvent evt) 

         {

  // Here we will ask what component called this method

              if (evt.getSource() == okButton) 

   

                   repaint();



 

     } 



}

 [/PHP]

i try to make a pogram that will change color base on the value enter by the user....i manage to compile and run it....but i decided to add the [COLOR="Blue"][SIZE="3"]container[/SIZE][/COLOR] ...so i mess up the code become -->

[PHP]import java.awt.*;

import java.applet.*;

import java.awt.event.*;

import javax.swing.*;





// Tells the applet you will be using the ActionListener methods.



public class GradeViewAssignment extends Applet implements ActionListener

{



     Button okButton;

     Button wrongButton;

     TextField nameField;

     private JButton red,blue, green, yellow, orange; // the JButtons which will cause the background colors to change

     private Container cp;     

     





     public void init() 

     {

  // Now we will use the FlowLayout

         // cp = getContentPane(); //NOTE!
          cp.setLayout(new FlowLayout());

          okButton = new Button("Grade");

          nameField = new TextField("Type Your exam mark here",35);

          cp.add(okButton);

          cp.add(nameField);



  // Attach actions to the components

          okButton.addActionListener(this);

          }



 // Here we will show the results of our actions

         public void paint(Graphics g)

         {

  

double aDouble = Double.parseDouble(nameField.getText());



          if (aDouble >= 80 && aDouble <= 100){
          cp.setBackground(Color.blue);
          }

 

          if (aDouble >= 75&& aDouble < 80){
          cp.setBackground(Color.green);

          } 
  

          if (aDouble >= 65 && aDouble < 75){
          cp.setBackground(Color.yellow);

          }

  

          g.drawString(nameField.getText(),20,100);

     }



 

        public void actionPerformed(ActionEvent evt) 

         {

  // user need to enter grade button

              if (evt.getSource() == okButton) 

                 repaint();



     } 



}

 
[/PHP]

i can't retrieve the container (see note comment there)...if i enable that line....it will give error....what should i do actually?


and how to add the text to the frame of applet...i did few search using google but i failed...i not able to use my java application knowledge to this applet...(and i just start to learn applet).....
what should i do to to make the program can display as attachment pic given below-->

---

### Post by mike_g on 2008-03-20
Well I never had a problem getting the content pane the way you are doing when using JFrames; another class that inherits Container.

You could try putting all your content inside a JPanel, setting your layout and stuff in the panel then add the panel at the end. I think that would work.

An easy way to add a line of text would be to use a JLabel. Something like:
```
JLabel grade = new JLabel("Your Grade Is: ");
add(grade);
```

Then to change the text do:
```
grade.setText("New Text");
```

---

