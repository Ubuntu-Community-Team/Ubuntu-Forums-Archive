---
title: "IOException in Java"
date: 2023-03-13
forum: Programming Talk
---

### Post by ronakmehta on 2023-03-13
I'm working on a simple Chat Bot software that replies to what the user enters. I'm keeping a text file with the questions it answers and the answers to those questions. I'm reading the file with a scanner. This is also just my second application in which I employ a graphical user interface to interact with the user. I've got a TextField, a Label, and two buttons (One to enter the question asked and the other to exit the program). As far as I understand Java GUIs, you must extend JFrame in the main class. Another programme I made for a graphical software that estimates the area of a rectangle is as follows:

```
[COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] java.[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit]awt[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit].*;[/FONT][/COLOR][COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR] javax.[FONT=inherit]swing[/FONT].*;
[COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR] java.[FONT=inherit]awt[/FONT].[FONT=inherit]event[/FONT].*;

public [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]RectangleProgram[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]extends[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JFrame[/FONT][/COLOR]
{
    private [COLOR=var(--highlight-keyword)][FONT=inherit]static[/FONT][/COLOR] final int [COLOR=var(--highlight-variable)][FONT=inherit]WIDTH[/FONT][/COLOR] = [COLOR=var(--highlight-namespace)][FONT=inherit]400[/FONT][/COLOR];
    private [COLOR=var(--highlight-keyword)][FONT=inherit]static[/FONT][/COLOR] final int [COLOR=var(--highlight-variable)][FONT=inherit]HEIGHT[/FONT][/COLOR] = [COLOR=var(--highlight-namespace)][FONT=inherit]200[/FONT][/COLOR];

    private [COLOR=var(--highlight-literal)][FONT=inherit]JLabel[/FONT][/COLOR] lengthL, widthL, areaL;
    private [COLOR=var(--highlight-literal)][FONT=inherit]JTextField[/FONT][/COLOR] lengthTF, widthTF, areaTF;
    private [COLOR=var(--highlight-literal)][FONT=inherit]JButton[/FONT][/COLOR] calculateB, exitB;

    [COLOR=var(--highlight-comment)][FONT=inherit]//Button handlers:[/FONT][/COLOR]
    private [COLOR=var(--highlight-literal)][FONT=inherit]CalculateButtonHandler[/FONT][/COLOR] cbHandler;
    private [COLOR=var(--highlight-literal)][FONT=inherit]ExitButtonHandler[/FONT][/COLOR] ebHandler;

    public [COLOR=var(--highlight-literal)][FONT=inherit]RectangleProgram[/FONT][/COLOR]()
    {
        lengthL = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JLabel[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Enter the length: "[/FONT][/COLOR], [COLOR=var(--highlight-literal)][FONT=inherit]SwingConstants[/FONT][/COLOR].[FONT=inherit]RIGHT[/FONT]);
        widthL = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JLabel[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Enter the width: "[/FONT][/COLOR], [COLOR=var(--highlight-literal)][FONT=inherit]SwingConstants[/FONT][/COLOR].[FONT=inherit]RIGHT[/FONT]);
        areaL = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JLabel[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Area: "[/FONT][/COLOR], [COLOR=var(--highlight-literal)][FONT=inherit]SwingConstants[/FONT][/COLOR].[FONT=inherit]RIGHT[/FONT]);

        lengthTF = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JTextField[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]10[/FONT][/COLOR]);
        widthTF = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JTextField[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]10[/FONT][/COLOR]);
        areaTF = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JTextField[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]10[/FONT][/COLOR]);

        [COLOR=var(--highlight-comment)][FONT=inherit]//SPecify handlers for each button and add (register) ActionListeners to each button.[/FONT][/COLOR]
        calculateB = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JButton[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Calculate"[/FONT][/COLOR]);
        cbHandler = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]CalculateButtonHandler[/FONT][/COLOR]();
        calculateB.[COLOR=var(--highlight-literal)][FONT=inherit]addActionListener[/FONT][/COLOR](cbHandler);
        exitB = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JButton[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Exit"[/FONT][/COLOR]);
        ebHandler = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]ExitButtonHandler[/FONT][/COLOR]();
        exitB.[COLOR=var(--highlight-literal)][FONT=inherit]addActionListener[/FONT][/COLOR](ebHandler);

        [COLOR=var(--highlight-literal)][FONT=inherit]setTitle[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Sample Title: Area of a Rectangle"[/FONT][/COLOR]);
        [COLOR=var(--highlight-literal)][FONT=inherit]Container[/FONT][/COLOR] pane = [COLOR=var(--highlight-literal)][FONT=inherit]getContentPane[/FONT][/COLOR]();
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]setLayout[/FONT][/COLOR]([COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]GridLayout[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]4[/FONT][/COLOR], [COLOR=var(--highlight-namespace)][FONT=inherit]3[/FONT][/COLOR]));

        [COLOR=var(--highlight-comment)][FONT=inherit]//Add things to the pane in the order you want them to appear (left to right, top to bottom)[/FONT][/COLOR]
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](lengthL);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](lengthTF);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](widthL);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](widthTF);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](areaL);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](areaTF);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](calculateB);
        pane.[COLOR=var(--highlight-literal)][FONT=inherit]add[/FONT][/COLOR](exitB);

        [COLOR=var(--highlight-literal)][FONT=inherit]setSize[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]WIDTH[/FONT][/COLOR], [COLOR=var(--highlight-variable)][FONT=inherit]HEIGHT[/FONT][/COLOR]);
        [COLOR=var(--highlight-literal)][FONT=inherit]setVisible[/FONT][/COLOR]([COLOR=var(--highlight-literal)][FONT=inherit]true[/FONT][/COLOR]);
        [COLOR=var(--highlight-literal)][FONT=inherit]setDefaultCloseOperation[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]EXIT_ON_CLOSE[/FONT][/COLOR]);
    }

    private [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]CalculateButtonHandler[/FONT][/COLOR] implements [COLOR=var(--highlight-literal)][FONT=inherit]ActionListener[/FONT][/COLOR]
    {
        public [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]actionPerformed[/FONT][/COLOR]([FONT=inherit]ActionEvent e[/FONT])
        {
            double width, length, area;
            length = [COLOR=var(--highlight-literal)][FONT=inherit]Double[/FONT][/COLOR].[COLOR=var(--highlight-literal)][FONT=inherit]parseDouble[/FONT][/COLOR](lengthTF.[COLOR=var(--highlight-literal)][FONT=inherit]getText[/FONT][/COLOR]()); [COLOR=var(--highlight-comment)][FONT=inherit]//We use the getText & setText methods to manipulate the data entered into those fields.[/FONT][/COLOR]
            width = [COLOR=var(--highlight-literal)][FONT=inherit]Double[/FONT][/COLOR].[COLOR=var(--highlight-literal)][FONT=inherit]parseDouble[/FONT][/COLOR](widthTF.[COLOR=var(--highlight-literal)][FONT=inherit]getText[/FONT][/COLOR]());
            area = length * width;
            areaTF.[COLOR=var(--highlight-literal)][FONT=inherit]setText[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]""[/FONT][/COLOR] + area);

        }
    }
    public [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]ExitButtonHandler[/FONT][/COLOR] implements [COLOR=var(--highlight-literal)][FONT=inherit]ActionListener[/FONT][/COLOR]
    {
        public [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]actionPerformed[/FONT][/COLOR]([FONT=inherit]ActionEvent e[/FONT])
        {
            [COLOR=var(--highlight-literal)][FONT=inherit]System[/FONT][/COLOR].[COLOR=var(--highlight-literal)][FONT=inherit]exit[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR]);
        }
    }

    public [COLOR=var(--highlight-keyword)][FONT=inherit]static[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]main[/FONT][/COLOR]([FONT=inherit][COLOR=var(--highlight-literal)][FONT=inherit]String[/FONT][/COLOR][] args[/FONT])
    {
        [COLOR=var(--highlight-literal)][FONT=inherit]RectangleProgram[/FONT][/COLOR] rectObj = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]RectangleProgram[/FONT][/COLOR]();
    } [COLOR=var(--highlight-color)][FONT=inherit]}[/FONT][/COLOR]
```

I'm using this application to experiment with alternative GUIs. It says I can't raise an IOException within the CalculateButtonHandler. I want to use a pretty similar structure for the Chat Bot software, however I'm curious whether there is a solution for the IOException, or if there is a better and easier approach to create a GUI?

---

