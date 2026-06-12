---
title: "NetBeans IDE 8.1 Couldn't connect to accessibility bus"
date: 2017-11-06
forum: Packaging and Compiling Programs
---

### Post by ddiggio on 2017-11-06
Hi everyone,
i was writing a simple code in Java with NetBeans IDE 8.1 to make a simple GUI but i encountered a problem while running the project;
the code is:

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JButton;

public class GUIQuizMate {

    public static void main(String[] args) {
        System.out.println("PROVA");
        JFrame frame = new JFrame("Quiz Matematica");
        JButton button = new JButton("Fai il quiz");
        JPanel panel = new JPanel();
        panel.add(button);
        frame.add(panel);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}

The output is: 

run:
PROVA

** (java:2196): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-TxusFOJQAt: Connessione rifiutata
BUILD STOPPED (total time: 10 seconds)

I also tried to use the terminal for compile and execute the program and i obtained this:

diggio@diggio-AOD257:~/NetBeansProjects/GUIQuizMate/src/guiquizmate$ javac GUIQuizMate.java
diggio@diggio-AOD257:~/NetBeansProjects/GUIQuizMate/src/guiquizmate$ java GUIQuizMate
Error: unable to find or load the main class GUIQuizMate
diggio@diggio-AOD257:~/NetBeansProjects/GUIQuizMate/src/guiquizmate$

I'm using Xubuntu 17.04
Can someone help me?

---

