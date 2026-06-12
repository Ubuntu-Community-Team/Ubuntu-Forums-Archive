---
title: "Java adding a .jar file in NetBeans"
date: 2011-09-23
forum: Programming Talk
---

### Post by rperalta2011 on 2011-09-23
I'm trying to graph two arrays of doubles. 

I was trying to use the  Chart2D_1.9.6k.jar  library, i added it in project preferences. 

But when i write:

import info.monitorenter.gui.chart.Chart2D;

or try to import any of the classes it says they do not exist. 

Is there an easier way to graph my data? Or what could i be doing wrong?

Here's my code:

import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import javax.swing.JFrame;
import javax.swing.JTextArea;
import javax.swing.JOptionPane;
import java.text.DecimalFormat;
import info.monitorenter.gui.chart.Chart2D;
import info.monitorenter.gui.chart.ITrace2D;
import info.monitorenter.gui.chart.traces.Trace2DSimple;

class Grafic
{
  public static void main(String[] args) {
    Double a = new Double(JOptionPane.showInputDialog(null, "a"));
    Double b = new Double(JOptionPane.showInputDialog(null, "b"));
    Double incrementoX = (b-a)/20;
    DecimalFormat formato = new DecimalFormat("0.000");
    String tabla = "x\tsinc(x)\n";
    Chart2D chart = new Chart2D();
    ITrace2D trace = new Trace2DSimple(); 
    chart.addTrace(trace);
    Double x=a;
    while (x <= b) {
      Double sinc;
      sinc = MiMate.sinc(x);
      tabla+= x+"\t"+formato.format(sinc)+"\n";
      trace.addPoint(x, sinc);
      x+= incrementoX;
    }
    JOptionPane.showMessageDialog(null, new JTextArea(tabla), "Tabla de Sinc(x) con "+a+"<=x<="+b, JOptionPane.PLAIN_MESSAGE);
    JFrame frame = new JFrame("Gr·fico de Sinc(x) con "+a+"<=x<="+b);
    frame.getContentPane().add(chart);
    frame.setSize(400,300);
    frame.addWindowListener( new WindowAdapter() {
      public void windowClosing(WindowEvent e) {
        System.exit(0);
      }
    }
    frame.setVisible(true);
  }
}

---

### Post by PaulM1985 on 2011-09-23
Is this the chart2d from sourceforge?  [http://chart2d.sourceforge.net/License.htm](http://chart2d.sourceforge.net/License.htm)  If so, you are using the wrong includes.  From the javadoc on the site you should be using net.sourceforge.chart2d.Chart2D for Chart2D.

Paul

---

