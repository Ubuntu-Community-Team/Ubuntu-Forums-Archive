---
title: "Repaint Method in Java"
date: 2009-11-15
forum: Programming Talk
---

### Post by eabod on 2009-11-15
Hello,

Why in the code below is the repaint method constantly called? I only want repaint to be called when the "Go" button is pushed.

```

import java.awt.*;
import java.applet.Applet;
import java.awt.Graphics;
import java.awt.event.*;
import java.io.BufferedReader;
import java.io.*;
import java.net.URL;
import java.net.*;
import javax.swing.Box;
import javax.swing.BoxLayout;


public class Assignment3 extends Applet implements ActionListener {

    String url;
    TextField inputLine = new TextField("Enter URL here.",15);
    TextArea console = new TextArea("", 6,80, TextArea.SCROLLBARS_VERTICAL_ONLY );
    Button pushButton = new Button("Go");

    public void paint (Graphics g) {
	String currentLine;
	URL target;
	int line = 1;
	int j, B=0;
	int[] kArray={}, wArray={}, x={};
	try {	    
	    target = new URL(url);
	    BufferedReader dis = new BufferedReader(new InputStreamReader(target.openStream()));
	    while (((currentLine = dis.readLine()) != null) && line <= 3) {
		if (line == 1) {
		    B = Integer.parseInt(currentLine);
		}
		else if (line == 2) {
		    String[] strk = currentLine.split("\t");
		    kArray = new int[strk.length];
		    for ( j = 0; j < strk.length;j++) {
			kArray[j] = Integer.parseInt(strk[j]);
		    }
		}
		else if (line == 3) {
		    String[] strw = currentLine.split("\t");
		    wArray = new int[strw.length];
		    for ( j = 0; j < strw.length;j++) {
			wArray[j] = Integer.parseInt(strw[j]);
		    }
		}
		line++;
	    }
 	    x= WtCoins(B, kArray, wArray);
	    for (j = 0; j < x.length; j++) {
		console.append(Integer.toString(x[j])+"\t");
	    }
	    console.append("\n");
	}
	catch (Exception e) {
	    if (url.equals(null) != true) {
		console.append("Error message: " + e.toString() + "\n");
	    }
	}
    }
    
    public Assignment3() {
	setLayout(new BoxLayout(this, BoxLayout.Y_AXIS));
	add(Box.createVerticalStrut(100));
	add(console);
	add(inputLine);
	add(pushButton);
	pushButton.addActionListener(this);
	console.setEditable(false);
    }


    public void init() {
	resize(500, 250);
    }
    public void actionPerformed(ActionEvent event) {
	url = inputLine.getText();
	repaint();
    }
    
    public int[] WtCoins(int B, int[] k, int[] w) {
	int[][] x = new int[B+1][k.length];
	int[] F = new int[B+1];
	int i, j, min, minIndex=0, s;
	for (j = 1; j <= B; j++) {
	    min = -1;
	    for (i = 0; i < k.length; i++) {
		if (k[i] <= j && F[j-k[i]] != -1) {
		    if (min == -1 || (w[i] + F[j-k[i]])< min) {
			    min = w[i] + F[j-k[i]];
			    minIndex = i;
		    }
		}
	    }
	    F[j] = min;
	    if (min != -1) {
		for (s = 0; s < k.length; s++) {
		    x[j][s] = x[j-k[minIndex]][s];
		}
		x[j][minIndex]++;
	    }
	    }
	return x[B];
    }
}

```

Thanks.

---

### Post by TennTux on 2009-11-15
I believe your problem may be the way the "paint" method works not the fact that you call "repaint" method in "actionPerformed".

I believe the key to understanding this is that "paint" is called every time the applet needs to be redrawn/displayed. And, this can happen for many reasons. e.g. The user minimizes the browser then restores it on the screen; Another window is displayed in front of the applet (does not require the whole applet to be obstructed only partial. This could even be your development environment/debugger). "paint" may be called once or a thousand times depending on what else is happening around your program and you have little control over when paint is controled.

Hope this helps.

---

