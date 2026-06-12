---
title: "problem in my java program"
date: 2011-04-11
forum: Programming Talk
---

### Post by greenmonkeey on 2011-04-11
hi guys help me out....there is some problems in my program...check it out for windows platform

> 
package browser;

import java.awt.*;
import java.awt.datatransfer.Clipboard;
import java.awt.datatransfer.StringSelection;
import java.awt.event.*;
import java.awt.print.PrinterJob;

import javax.swing.*;
import javax.swing.border.*
import javax.swing.event.*;
import javax.swing.text.*;

import java.io.*;
import java.net.URL;
import java.util.*;
import javax.swing.text.html.*;

public class Genxplora extends JPanel 
    {
            public JMenuBar menubar;
            public JEditorPane jep;
            final JLabel statusbar;
            public JToolBar tool_bar;
            JTextField urlfield;
            //CheckboxMenuItem add_bar;
            //CheckboxMenuItem sta_bar;
            JComboBox combo;
            static JTextField ta;
            
            JScrollPane jsp=new JScrollPane(jep);
            JButton go;

            private Stack urlstack=new Stack();
            private Stack urlstack1=new Stack();

            private JTextComponent textComp;
          Clipboard clipbd = getToolkit().getSystemClipboard();
       	PrinterJob prtMe = PrinterJob.getPrinterJob();


         







   public Genxplora()
            {
                   menubar=new JMenuBar();
                   JPanel urlpanel=new JPanel();
                  
                   urlpanel.setLayout(new BorderLayout());
                   statusbar=new JLabel(" Status Bar ");
                   jep=new JEditorPane();
                  
                   textComp=createTextComponent();

                   demoaction back=new demoaction("Back",new ImageIcon("PreviousArrow.gif"),"back",'b');
                   demoaction forward=new demoaction("Forward",new ImageIcon("NextArrow.gif "),"forward",'f');
                   demoaction stop=new demoaction("Stop",new ImageIcon("STOPSML.gif "),"stop",'s');
                   demoaction refresh=new demoaction("Refresh",new ImageIcon("return.gif "),"refresh",'r');
                   demoaction home=new demoaction("Home",new ImageIcon("web.gif"),"home",'h');
                   demoaction help=new demoaction("Help",new ImageIcon("help.gif"),"help",'p');
                   

                    JMenu file=new JMenu("File");
                   JMenuItem it1,it2,it3,it4,it5,it6,it7,it8,it9;

                   JMenu sub=new JMenu("New");
                   sub.add(it1=new JMenuItem("Window"));
                   it1.setEnabled(true);
                   file.add(sub);

                   file.add(it2=new JMenuItem("Open..."));
                   file.add(it3=new JMenuItem("Save"));
                   it3.setEnabled(true);
                   file.add(it4=new JMenuItem("Save As..."));
                   file.add(new JMenuItem().add(new JSeparator()));
              //     file.add(it5=new JMenuItem("Page Setup..."));
                //   it5.setEnabled(true);
                   file.add(it6=new JMenuItem("Print..."));
                   it6.setEnabled(true);
                  // file.add(it7=new JMenuItem("Print Preview..."));
                   //it7.setEnabled(true);
                   file.add(new JMenuItem().add(new JSeparator()));
                   //file.add(it8=new JMenuItem("Send"));
                   //it8.setEnabled(true);
                   file.add(new JMenuItem().add(new JSeparator()));
                   file.add(it9=new JMenuItem("Close"));

                   menubar.add(file);

                    JMenu edit=new JMenu("Edit");
                     JMenuItem ite1,ite3,ite4,ite5,ite6,ite7,ite8,ite9;
                    JMenuItem ite2;
                   edit.add(ite1=new JMenuItem("Cut"));
                   ite1.setEnabled(false);
                   edit.add(ite2=new JMenuItem("Copy"));
                   ite2.setEnabled(false);
                   edit.add(ite3=new JMenuItem("Paste"));
                   ite3.setEnabled(false);
                   edit.add(new JMenuItem().add(new JSeparator()));
                   edit.add(ite4=new JMenuItem("Select All"));
                   ite4.setEnabled(true);
                   edit.add(ite5=new JMenuItem("Find(on this Page)..."));
                   ite5.setEnabled(true);

                   menubar.add(edit);


                   JMenu view=new JMenu("View");
                   JMenuItem itv1,itv2,itv3,itv4,itv5,itv6,itv7,itv8,itv9;

                  /* JMenu sub1=new JMenu("tool_go");
                   add_bar=new CheckboxMenuItem("Address bar");

                   sta_bar=new CheckboxMenuItem("Status Bar");
                   
                   view.add(sub1);
*/
                   view.add(new JMenuItem().add(new JSeparator()));

                   JMenu sub2=new JMenu("Go To");
                   sub2.add(back);
                   sub2.add(forward);
                   sub2.add(new JMenuItem().add(new JSeparator()));
                   sub2.add(home);
                   sub2.add(new JMenuItem().add(new JSeparator()));
                   view.add(sub2);

                   view.add(stop);
                   view.add(refresh);
                   view.add(new JMenuItem().add(new JSeparator()));

                   view.add(itv1=new JMenuItem("Full Screen"));
                   menubar.add(view);


                   JMenu help1=new JMenu("Help");
                   JMenuItem tip=new JMenuItem("tip of the day");
                   JMenuItem about=new JMenuItem("about browser");
                   help1.add(tip);
                   help1.add(about);
                   menubar.add(help1);

                   myhandler handler=new myhandler(this);

                   it1.addActionListener(handler);
                   it2.addActionListener(handler);
                   it3.addActionListener(handler);
                   it4.addActionListener(handler);
                  // it5.addActionListener(handler);
                   it6.addActionListener(handler);
                   //it7.addActionListener(handler);
                   //it8.addActionListener(handler);
                   it9.addActionListener(handler);
                   ite1.addActionListener(handler);
                   ite2.addActionListener(handler);
                   ite3.addActionListener(handler);
                   ite4.addActionListener(handler);
                   ite5.addActionListener(handler);
                   itv1.addActionListener(handler);
                   tip.addActionListener(handler);
                   about.addActionListener(handler);

                   tool_bar=new JToolBar(" Tool");
                   tool_bar.add(back);
                   tool_bar.add(forward);
                   tool_bar.add(new JSeparator());

                   tool_bar.add(stop);
                   tool_bar.add(refresh);
                   tool_bar.add(home);
                   home.setEnabled(false);

                  
                   tip.setEnabled(true);
                   about.setEnabled(true);

                   JLabel label=new JLabel("Address");
                   tool_bar.add(label);
                   
                   String lst[]={"http://localhost/java_site1.html","http://localhost/html_parse.html","http://localhost/java_site.html"};
                   urlfield=new JTextField();
                                                                                       
                   urlfield.addActionListener(new ActionListener()
                                           {
                                                 public void actionPerformed(ActionEvent ae)
                                                 {
                                                     try
                                                     {

                                                            urlstack.push(urlfield.getText());
                                                           // urlstack1.push(urlfileld.getText());
                                                            urlfield.setText(urlfield.getText());
                                                            jep.setPage( urlfield.getText());
                                                            statusbar.setText( urlfield.getText());
                                                            jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                                                     }
                                                     catch(IOException e)
                                                     {
                                                            jep.setText("ERROR OPENING REQUESTED PAGE......\n\n"+e);
                                                            JOptionPane.showMessageDialog(Genxplora.this,"Requested  Page Not Found.....","ERROR",JOptionPane.ERROR_MESSAGE);
                                                     }
                                                            
                                             }

                                    });

                    tool_bar.add(urlfield);
                    
                    go=new JButton("Go");
                    

                    go.addActionListener(new ActionListener()
                                      {
                                            public void actionPerformed(ActionEvent ae)
                                            {
                                                     try
                                                     {
                                                    	 urlstack.push(urlfield.getText());
                                                         // urlstack1.push(urlfileld.getText());
                                                          urlfield.setText(urlfield.getText());
                                                          jep.setPage( urlfield.getText());
                                                          statusbar.setText( urlfield.getText());
                                                          jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                                                     }
                                                     catch(IOException e)
                                                     {
                                                            jep.setText("ERROR...........\n\n"+e);
                                                            JOptionPane.showMessageDialog(Genxplora.this,"Requested  Page Not Found.....","ERROR",JOptionPane.ERROR_MESSAGE);
                                                     }
                                                  
                                            }
                                     });

                    tool_bar.add(go);  

                    jep.addHyperlinkListener(new HyperlinkListener()
                                         {
                                               public void hyperlinkUpdate(HyperlinkEvent he)
                                               {
                                                     if(he.getEventType()==HyperlinkEvent.EventType.ACTIVATED)
                                                     {
                                                          try
                                                          {
                                                        	  urlstack.push(urlfield.getText());
                                                              // urlstack1.push(urlfileld.getText());
                                                               urlfield.setText(urlfield.getText());
                                                               jep.setPage( urlfield.getText());
                                                               statusbar.setText( urlfield.getText());
                                                               jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                                                          }
                                                          catch(IOException e)
                                                          {
                                                                jep.setText("ERROR OPENING HYPERLINK..........\n\n"+e);
                                                                statusbar.setText("Error Opening Hyperlink.......");
                                                                JOptionPane.showMessageDialog(Genxplora.this,"Requested  Page Not Found.....","ERROR",JOptionPane.ERROR_MESSAGE);
                                                          }
                                                     }
                                               }
                                         });

     }                  

       public static void main(String s[]) throws IOException
       {
              Genxplora tool=new Genxplora();
             

              tool.jep=new JEditorPane();
              tool.jep.setPreferredSize(new Dimension(790,448));
              tool.jep.setBorder(new BevelBorder(BevelBorder.LOWERED));

              tool.tool_bar.setMaximumSize(tool.tool_bar.getSize());
              
                         
              JFrame frame=new JFrame("Genxplora");


              frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

              frame.setJMenuBar(tool.menubar);
              frame.getContentPane().add(tool.tool_bar,BorderLayout.NORTH);
              frame.getContentPane().add(tool.jep,BorderLayout.CENTER);
              frame.getContentPane().add(tool.statusbar,BorderLayout.SOUTH);
              frame.pack();
              frame.setVisible(true);


                  tool.jep.setEditable(false);

      }   //end of class main




      class demoaction extends AbstractAction
      {
             public demoaction(String text,Icon icon,String descri,char acc)
             {
                    super(text,icon);
                    putValue(ACCELERATOR_KEY,KeyStroke.getKeyStroke(acc,Toolkit.getDefaultToolkit().getMenuShortcutKeyMask()));
                    putValue(SHORT_DESCRIPTION,descri);
             }

             // BackWard Button

             public void actionPerformed(ActionEvent             ae)
             {
                      if(ae.getActionCommand()=="Back")
                      {
                            if(urlstack.size()<0)
                            {
                                 statusbar.setText("No Page available....");
                                 return;
                            }

                             try
                             {
                            	 urlstack.push(urlfield.getText());
                                 // urlstack1.push(urlfileld.getText());
                                  urlfield.setText(urlfield.getText());
                                  jep.setPage( urlfield.getText());
                                  statusbar.setText( urlfield.getText());
                                  jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                             }
                             catch(IOException e)
                             {
                                   jep.setText("ERROR......"+e);
                                   JOptionPane.showMessageDialog(Genxplora.this,"Back Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                             }
                      }


                  //Forward Button Coding

                      if(ae.getActionCommand()=="Forward")
                      {
                            if(urlstack1.size()<0)
                            {
                                 statusbar.setText("No Page available...");
                                 return;
                            }

                             try
                             {
                                   urlstack.push(urlstack1.pop());
                                   String urlstring=(String) urlstack1.peek();
                                   urlfield.setText(urlstring);
                                   jep.setPage(urlstring);
                                   jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                             }
                             catch(IOException e)
                             {
                                   jep.setText("ERROR.........\n\n"+e);
                                   JOptionPane.showMessageDialog(Genxplora.this,"Forward Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                             }
                      }


                   // Coding for stop

                    if(ae.getActionCommand()=="Stop")
                    {
                             try
                             {
                                     urlstack.pop();
                                     String str=(String)urlstack.peek();
                                     urlfield.setText(str);
                                     jep.setPage(str);
                                     jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                                     statusbar.setText(str);
                              }
                              catch(IOException e)
                              {
                                     statusbar.setText("ERROR....in stopping ");
                                     JOptionPane.showMessageDialog(Genxplora.this,"Stop Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                              }
                    }   //end of stop


               //Coding of Refresh

                  if(ae.getActionCommand()=="Refresh")
                  {
                           try
                           {
                                    String str=(String)urlstack.peek();
                                    urlfield.setText(str);
                                    jep.setPage(str);
                                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                                    statusbar.setText("Refreshed site...."+str);
                            }
                            catch(IOException e)
                            {
                                    jep.setText("ERROR IN REFRESHING PAGE......");
                                    statusbar.setText("ERROR IN REFRESHING REQUESTED PAGE......");
                                    JOptionPane.showMessageDialog(Genxplora.this,"Refresh Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                            }
                   }//end of refresh

            }   //end of action performed
             
      }      //end of class demoaction


class myhandler implements ActionListener
      {
             Genxplora tool;

             public myhandler(Genxplora tool)
             {
                   this.tool=tool;
             }

             public void actionPerformed(ActionEvent ae)
             {
            	 
            	 if(ae.getActionCommand()=="Window")
            	 {
            		
            		 Genxplora tool1= new Genxplora();
            		
            		 tool1.jep=new JEditorPane();
                     tool1.jep.setPreferredSize(new Dimension(790,448));
                     tool1.jep.setBorder(new BevelBorder(BevelBorder.LOWERED));

                     tool1.tool_bar.setMaximumSize(tool1.tool_bar.getSize());
                     JFrame frame1=new JFrame("Genxplore");
                   

                     frame1.setJMenuBar(tool1.menubar);
                     frame1.getContentPane().add(tool1.tool_bar,BorderLayout.NORTH);
                     frame1.getContentPane().add(tool1.jep,BorderLayout.CENTER);
                     frame1.getContentPane().add(tool1.statusbar,BorderLayout.SOUTH);
                     frame1.pack();
                     frame1.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                     frame1.setVisible(true);


                         tool1.jep.setEditable(false);

            	 }
                  if(ae.getActionCommand()=="Close")
                       System.exit(0);

                  //Event Handling for Open button

                 if(ae.getActionCommand()=="Open...")
                  {
                         JFileChooser chooser=new JFileChooser();
                         chooser.setMultiSelectionEnabled(true);
                         int option=chooser.showOpenDialog(Genxplora.this);
                         if(option==JFileChooser.APPROVE_OPTION)
                         {
                               File[] sf=chooser.getSelectedFiles();
                               String flst="nothing";

                               if(sf.length > 0)
                                    flst=sf[0].getName();

                               for(int i=1;i<sf.length ;++i)
                                    flst+=","+sf[i].getName();

                               try
                               {
                                      urlfield.setText("http://localhost/"+flst);
                                      jep.setPage("http://localhost/"+flst);
                                      statusbar.setText("http://localhost/"+flst);
                                      jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                               }
                               catch(IOException e)
                               {
                                      jep.setText("ERROR........"+e);
                                      JOptionPane.showMessageDialog(Genxplora.this,"Error opening requested document.....","ERROR",JOptionPane.ERROR_MESSAGE);
                                }

                         }
                         else
                         {
                                 System.out.println("You Canceled");
                         }
                  }  
                  if(ae.getActionCommand()=="Save")
                  {
                	  JFileChooser fc = new JFileChooser();
      				int returnVal = fc.showSaveDialog(Genxplora.this);
      				if(returnVal == JFileChooser.APPROVE_OPTION)
      				{
      					String savefile = fc.getSelectedFile().getPath();
      					if(savefile == null)
      					{
      					    return;
      					}
      					else
      					{
      						String docToSave = jep.getText();
if(docToSave != null)
      						{
      							FileOutputStream fstrm = null;
      							BufferedOutputStream ostrm = null;
      							try
      							{
      								fstrm = new FileOutputStream(savefile);
      								ostrm = new BufferedOutputStream(fstrm);
      								byte[] bytes = null;
      								try
      								{
      									bytes = docToSave.getBytes();
      								}
      								catch(Exception e1)
      								{
      									e1.printStackTrace();
      								}
      								ostrm.write(bytes);
      							}
      					   	catch(IOException io)
      					   	{
      					   		System.err.println("IOException: " +
      					   				io.getMessage());
      					   	}
      					   	finally
      					   	{
      								try
      								{
      									ostrm.flush();
      									fstrm.close();
      									ostrm.close();
      								}
      								catch(IOException ioe)
      								{
      									System.err.println("IOException: " +
      											ioe.getMessage());
      								}
      							}
      						}
      					}
      				}
      				else
      				{
      					return;
      				}
      			
                  }
                 if(ae.getActionCommand()=="Save As...")
                 {
                        JFileChooser chooser=new JFileChooser();

                        if(chooser.showSaveDialog(Genxplora.this)!=JFileChooser.APPROVE_OPTION)
                                         return;
                        File file=chooser.getSelectedFile();
                        if(file==null)
                               return;
                        FileWriter writer=null;
                        try
                        {
                               writer=new FileWriter(file);
                               textComp.write(writer);
                        }
                        catch(IOException e)
                        {
                                 JOptionPane.showMessageDialog(Genxplora.this,"File not saved","ERROR",JOptionPane.ERROR_MESSAGE);
                        }
                        finally
                        {
                                if(writer!=null)
                                try
                                {
                                      writer.close();
                                }
                                catch(IOException e)
                                {}
                        }

               }
                        
                 /*if(ae.getActionCommand()=="Page Setup...")
      				try
      				{
      					prtMe.printDialog();
      				}
      				catch(Exception ew)
      				{
      				}*/
            		 if(ae.getActionCommand()=="Print...")
     				try
     				{
     					prtMe.printDialog();
     				}
     				catch(Exception ew)
     				{
     				}
           		 if(ae.getActionCommand()=="Copy")
      				try
      				{
      					String selection = jep.getSelectedText();
      					StringSelection clipString = new StringSelection(selection);
      					clipbd.setContents(clipString, clipString);
      				}
      				catch(Exception ew)
      				{
      				}

           		
            
      				 if(ae.getActionCommand()=="Select All")
           				try
           				{
           					jep.selectAll();
           				}
           				catch(Exception ew)
           				{
           				}
           			
           			 if(ae.getActionCommand()=="Find(on this page)...")
           				try
           				{
           					String find = "";
           					find = JOptionPane.showInputDialog(
           							"Find on this page: ");
           				}
           				catch(Exception ew)
           				{
           				}
              			 if(ae.getActionCommand()=="Full Screen")
              			 {
              				 tool.jep.setPreferredSize(new Dimension(900,900));
              				
              			 }
           			 

           			if(ae.getActionCommand()=="about browser")
          			 {
           				JOptionPane.showMessageDialog(Genxplora.this,"Version no:101bgjy1" 
           						 
           						,"ABOUT BROWSER",JOptionPane.INFORMATION_MESSAGE);
          			 }
             }
             
            public void itemStateChanged(ItemEvent ie)
             {
                 
             }
      }            



protected JTextComponent createTextComponent()
{
        JTextArea ta=new JTextArea();
        ta.setLineWrap(true);
        return ta;
} 


      class MyWindowAdapter extends WindowAdapter
      {
             Genxplora tool;
             public MyWindowAdapter(Genxplora tool)
             {
                  this.tool=tool;
             }
             public void windowClosing(WindowEvent we)
             {
                  
             }
      } 

                     
}          
      
 


class SimpleLinkListener implements HyperlinkListener
{
      private JEditorPane pane;
      private JTextField urlfield;
      private JComboBox combox;
      private JLabel statusbar;


      public SimpleLinkListener(JEditorPane jep,JTextField jtf,JLabel j1)
      {
           pane=jep;
           urlfield=jtf;
           statusbar=j1;
      }
      public SimpleLinkListener(JEditorPane jep)
      {
          this(jep,null,null);
      }


      public void hyperlinkUpdate(HyperlinkEvent he)
      {
            HyperlinkEvent.EventType type = he.getEventType();
            if (type == HyperlinkEvent.EventType.ENTERED)
            {
                  if (statusbar != null)
                  {
                        statusbar.setText(he.getURL().toString());
                  }
            }

            else if(type == HyperlinkEvent.EventType.EXITED)
            {
                   if (statusbar != null)
                   {
                        statusbar.setText(" ");
                   }
            }
            else if(type == HyperlinkEvent.EventType.ACTIVATED)
            {
                    if (he instanceof HTMLFrameHyperlinkEvent)
                    {
                           HTMLFrameHyperlinkEvent evt=(HTMLFrameHyperlinkEvent)he; 
                           HTMLDocument doc=(HTMLDocument)pane.getDocument();
                           doc.processHTMLFrameHyperlinkEvent(evt);
                    }
                   }
else
                    {
                           try
                           {
                                pane.setPage(he.getURL());
                                if (urlfield!=null)
                                {
                                       urlfield.setText(he.getURL().toString());

                                }
                           }
                       

  catch(FileNotFoundException e)
                           {
                                  pane.setText("Could not open file : <tt>"+he.getURL()+"</tt>.<hr>");
                           }
                          
 catch(Exception e)
                           {
                                  e.printStackTrace();
                           }
                    }
             }
        }

---

### Post by PaulM1985 on 2011-04-11
Could you describe what the problem is?

Could you put your code in [CODE] tags?

---

### Post by greenmonkeey on 2011-04-11
hv u run the program?it must hv shown u some errors....actually i can't run it successfully...i want to run it

---

### Post by greenmonkeey on 2011-04-11
the error is -recompile with xlint and whn i did so it says unable to create jvm

---

### Post by Some Penguin on 2011-04-11
[http://ubuntuforums.org/showthread.php?t=1006666]("http://ubuntuforums.org/showthread.php?t=1006666")

In particular,

[http://catb.org/~esr/faqs/smart-questions.html]("http://catb.org/~esr/faqs/smart-questions.html")

---

### Post by greenmonkeey on 2011-04-11
i think its time to solve my problem guys pls?

---

### Post by Zugzwang on 2011-04-11
> **greenmonkeey said:**
> i think its time to solve my problem guys pls?

First thing: *always* copy and paste the full error message. People here will only copy&paste your code and try to compile it if it isn't obvious what is wrong. 

Second thing: "recompile with xlint" is not an error, just a warning. Copy&Paste the original message into google and you will find a lot of forum threads explaining it.

Third thing: "unable to create jvm" is probably no problem with your program but rather with the execution environment. Try to compile & run the program from the terminal. How this can be done is explained in the stickies.

---

### Post by Some Penguin on 2011-04-11
> **greenmonkeey said:**
> i think its time to solve my problem guys pls?

No; it's time to permanently ignore the poster who won't read the stickies, posts a giant wall of code, and puts zero effort into actually giving providing concise, relevant details of the problem while demonstrating an unearned sense of entitlement.

---

### Post by greenmonkeey on 2011-04-11
my errors



main.java:19: class Genxplora is public, should be declared in a file named Genxplora.java
public class Genxplora extends JPanel 
       ^
Note: main.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.

---

### Post by r-senior on 2011-04-11
> **greenmonkeey said:**
> 
```
main.java:19: class Genxplora is public, should be declared in a file named Genxplora.java
```

Is the name of your file Genxplora.java? Or is it called main.java, perchance?

> ```

Note: Recompile with -Xlint:unchecked for details.
```
How about recompiling with -Xlint:unchecked and see if it gives you any details?

```

$ javac -Xlint:unchecked Genxplora.java

```

---

### Post by greenmonkeey on 2011-04-11
i recompile it

main.java:19: class Genxplora is public, should be declared in a file named Genxplora.java
public class Genxplora extends JPanel 
       ^
main.java:196: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                                            urlstack.push(urlfield.getText());
                                                                         ^
main.java:224: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                                    	 urlstack.push(urlfield.getText());
                                                    	              ^
main.java:250: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                                        	  urlstack.push(urlfield.getText());
                                                        	               ^
main.java:324: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                            	 urlstack.push(urlfield.getText());
                            	              ^
main.java:351: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                   urlstack.push(urlstack1.pop());
                                                ^
1 error
5 warnings

---

### Post by r-senior on 2011-04-11
> **greenmonkeey said:**
> [COLOR="Red"]**main.java**[/COLOR]:19: class Genxplora is public, [COLOR="Red"]**should be**[/COLOR] declared in a file named [COLOR="Red"]**Genxplora.java**[/COLOR]
There's a clue in the error message. I've highlighted it in red. Let us know if you are still stuck.

---

### Post by greenmonkeey on 2011-04-11
i still didnt get it dude...

actually thing is i m a newbie to java prog..can u tell me where to make changes in the program...

---

### Post by simeon87 on 2011-04-11
> **greenmonkeey said:**
> i still didnt get it dude...

actually thing is i m a newbie to java prog..can u tell me where to make changes in the program...

Read the error message: you need to rename the Java file. What more can we do if you don't follow the instructions in the error message?

---

### Post by Guppey on 2011-04-11
what you declare as the name in the code is what the name of the .java file needs to be. for example:
```
public class Genxplora extends JPanel
```
the name of the .java file should be 
```
Genxplora.java
```

---

### Post by NovaAesa on 2011-04-12
Type in ```
mv currentname.java Genxplora.java
``` where currentname.java is the current name of the java file.

---

### Post by ve4cib on 2011-04-12
Backing up, and hopefully providing a little more clarity for the original poster...

In Java the name of the file is VERY important.  The filename and the name of the public class within it MUST match.

So if your code contains:

```
public class MyFirstClass {
    ...
}
```

You must save your file as "MyFirstClass.java"  Saving the file with any other filename will result in the error you are seeing.

It looks like you've saved your java file as "main.java" but the class you've declared is called "Genxplora"  You need to rename your java file so that the filename is "Genxplora.java"

Open it up in Gedit, Notepad, or whatever program you used to write the code, and go File > Save As..., type in "Genxplora.java" and hit save.  Then try recompiling the program and see if it works.


Also, if you're a complete beginner when it comes to Java, you may find this website useful: 

[http://webmail.cs.umanitoba.ca/mediawiki/index.php/COMP1010](http://webmail.cs.umanitoba.ca/mediawiki/index.php/COMP1010)

It's a wiki/textbook written by third-year Computer Science students for first-year students learning Java.  It assumes you know nothing about programming, and starts from the basics.  You might find going through the exercises helpful if you're just starting out.

---

### Post by greenmonkeey on 2011-04-12
javac Genxplora.java
Genxplora.java:50: invalid method declaration; return type required
   public Genxplora()

---

### Post by greenmonkeey on 2011-04-12
this is the error when i compile it with xlint


javac -Xlint:unchecked Genxplora.java
Genxplora.java:196: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                                            urlstack.push(urlfield.getText());
                                                                         ^
Genxplora.java:224: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                                    	 urlstack.push(urlfield.getText());
                                                    	              ^
Genxplora.java:250: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                                        	  urlstack.push(urlfield.getText());
                                                        	               ^
Genxplora.java:324: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                            	 urlstack.push(urlfield.getText());
                            	              ^
Genxplora.java:351: warning: [unchecked] unchecked call to push(E) as a member of the raw type java.util.Stack
                                   urlstack.push(urlstack1.pop());
                                                ^
5 warnings

---

### Post by NovaAesa on 2011-04-12
Those warnings just mean you aren't using generics correctly with your container class. The solution would be to specify a type when declaring your stack.

---

### Post by SevenMachines on 2011-04-12
As NovaAesa says!
 
Couple more points

* Warnings are not errors! always be clear about the two. Errors mean you're wrong, warnings mean you're probably wrong :) but can be  of the variety
 > compiler: 'are you sure you really want to do this?'  
programmer: 'yes, yes i honestly meant to do that! I never make mistakes!!'You might want to look over your generics, they've been around for a while now...
[http://download.oracle.com/javase/tutorial/java/generics/index.html](http://download.oracle.com/javase/tutorial/java/generics/index.html)
...maybe a couple of other things too, classname-filename and packagename-directory structure are quite fundamental.

Quick example, stack1 will give an unchecked warning, stack2 is declared properly with Stack<String> so is fine

Test.java:
```
import java.util.Stack;

class Test{
    public static void main(String s[]){
        // Old non-generic stack
        Stack stack1=new Stack();

        // New generic stack
        Stack<String> stack2=new Stack<String>();

        // Unchecked warning
        stack1.push("not generic");

        // Type properly specified so no warning
        stack2.push("This is generics!");
    }
}
```

---

### Post by DarkHackerX on 2011-04-29
Try compiling this version. This version compile for me with no problems. Just run 
"
$ javac Genxplora.java 
$ java Genxplora
"
The warning and errors should be gone. Oh and +1 with above.

```

import java.awt.*;
import java.awt.datatransfer.Clipboard;
import java.awt.datatransfer.StringSelection;
import java.awt.event.*;
import java.awt.print.PrinterJob;

import javax.swing.*;
import javax.swing.border.*;
import javax.swing.event.*;
import javax.swing.text.*;

import java.io.*;
import java.net.URL;
import java.util.*;
import javax.swing.text.html.*;

public class Genxplora extends JPanel
{
    public JMenuBar menubar;
    public JEditorPane jep;
    final JLabel statusbar;
    public JToolBar tool_bar;
    JTextField urlfield;
    //CheckboxMenuItem add_bar;
    //CheckboxMenuItem sta_bar;
    JComboBox combo;
    static JTextField ta;

    JScrollPane jsp=new JScrollPane(jep);
    JButton go;

    private Stack<String> urlstack=new Stack<String>();
    private Stack<String> urlstack1=new Stack<String>();

    private JTextComponent textComp;
    Clipboard clipbd = getToolkit().getSystemClipboard();
    PrinterJob prtMe = PrinterJob.getPrinterJob();

    public Genxplora()
    {
        menubar=new JMenuBar();
        JPanel urlpanel=new JPanel();

        urlpanel.setLayout(new BorderLayout());
        statusbar=new JLabel(" Status Bar ");
        jep=new JEditorPane();

        textComp=createTextComponent();

        demoaction back=new demoaction("Back",new ImageIcon("PreviousArrow.gif"),"back",'b');
        demoaction forward=new demoaction("Forward",new ImageIcon("NextArrow.gif "),"forward",'f');
        demoaction stop=new demoaction("Stop",new ImageIcon("STOPSML.gif "),"stop",'s');
        demoaction refresh=new demoaction("Refresh",new ImageIcon("return.gif "),"refresh",'r');
        demoaction home=new demoaction("Home",new ImageIcon("web.gif"),"home",'h');
        demoaction help=new demoaction("Help",new ImageIcon("help.gif"),"help",'p');


        JMenu file=new JMenu("File");
        JMenuItem it1,it2,it3,it4,it5,it6,it7,it8,it9;

        JMenu sub=new JMenu("New");
        sub.add(it1=new JMenuItem("Window"));
        it1.setEnabled(true);
        file.add(sub);

        file.add(it2=new JMenuItem("Open..."));
        file.add(it3=new JMenuItem("Save"));
        it3.setEnabled(true);
        file.add(it4=new JMenuItem("Save As..."));
        file.add(new JMenuItem().add(new JSeparator()));
        // file.add(it5=new JMenuItem("Page Setup..."));
        // it5.setEnabled(true);
        file.add(it6=new JMenuItem("Print..."));
        it6.setEnabled(true);
        // file.add(it7=new JMenuItem("Print Preview..."));
        //it7.setEnabled(true);
        file.add(new JMenuItem().add(new JSeparator()));
        //file.add(it8=new JMenuItem("Send"));
        //it8.setEnabled(true);
        file.add(new JMenuItem().add(new JSeparator()));
        file.add(it9=new JMenuItem("Close"));

        menubar.add(file);

        JMenu edit=new JMenu("Edit");
        JMenuItem ite1,ite3,ite4,ite5,ite6,ite7,ite8,ite9;
        JMenuItem ite2;
        edit.add(ite1=new JMenuItem("Cut"));
        ite1.setEnabled(false);
        edit.add(ite2=new JMenuItem("Copy"));
        ite2.setEnabled(false);
        edit.add(ite3=new JMenuItem("Paste"));
        ite3.setEnabled(false);
        edit.add(new JMenuItem().add(new JSeparator()));
        edit.add(ite4=new JMenuItem("Select All"));
        ite4.setEnabled(true);
        edit.add(ite5=new JMenuItem("Find(on this Page)..."));
        ite5.setEnabled(true);

        menubar.add(edit);


        JMenu view=new JMenu("View");
        JMenuItem itv1,itv2,itv3,itv4,itv5,itv6,itv7,itv8,itv9;

        /* JMenu sub1=new JMenu("tool_go");
add_bar=new CheckboxMenuItem("Address bar");

sta_bar=new CheckboxMenuItem("Status Bar");

view.add(sub1);
         */
        view.add(new JMenuItem().add(new JSeparator()));

        JMenu sub2=new JMenu("Go To");
        sub2.add(back);
        sub2.add(forward);
        sub2.add(new JMenuItem().add(new JSeparator()));
        sub2.add(home);
        sub2.add(new JMenuItem().add(new JSeparator()));
        view.add(sub2);

        view.add(stop);
        view.add(refresh);
        view.add(new JMenuItem().add(new JSeparator()));

        view.add(itv1=new JMenuItem("Full Screen"));
        menubar.add(view);


        JMenu help1=new JMenu("Help");
        JMenuItem tip=new JMenuItem("tip of the day");
        JMenuItem about=new JMenuItem("about browser");
        help1.add(tip);
        help1.add(about);
        menubar.add(help1);

        myhandler handler=new myhandler(this);

        it1.addActionListener(handler);
        it2.addActionListener(handler);
        it3.addActionListener(handler);
        it4.addActionListener(handler);
        // it5.addActionListener(handler);
        it6.addActionListener(handler);
        //it7.addActionListener(handler);
        //it8.addActionListener(handler);
        it9.addActionListener(handler);
        ite1.addActionListener(handler);
        ite2.addActionListener(handler);
        ite3.addActionListener(handler);
        ite4.addActionListener(handler);
        ite5.addActionListener(handler);
        itv1.addActionListener(handler);
        tip.addActionListener(handler);
        about.addActionListener(handler);

        tool_bar=new JToolBar(" Tool");
        tool_bar.add(back);
        tool_bar.add(forward);
        tool_bar.add(new JSeparator());

        tool_bar.add(stop);
        tool_bar.add(refresh);
        tool_bar.add(home);
        home.setEnabled(false);


        tip.setEnabled(true);
        about.setEnabled(true);

        JLabel label=new JLabel("Address");
        tool_bar.add(label);

        String lst[]={"http://localhost/java_site1.html","http://localhost/html_parse.html","http://localhost/java_site.html"};
        urlfield=new JTextField();

        urlfield.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent ae)
            {
                try
                {

                    urlstack.push(urlfield.getText());
                    // urlstack1.push(urlfileld.getText());
                    urlfield.setText(urlfield.getText());
                    jep.setPage( urlfield.getText());
                    statusbar.setText( urlfield.getText());
                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                }
                catch(IOException e)
                {
                    jep.setText("ERROR OPENING REQUESTED PAGE......\n\n"+e);
                    JOptionPane.showMessageDialog(Genxplora.this,"Requ ested Page Not Found.....","ERROR",JOptionPane.ERROR_MESSAGE);
                }

            }

        });

        tool_bar.add(urlfield);

        go=new JButton("Go");


        go.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent ae)
            {
                try
                {
                    urlstack.push(urlfield.getText());
                    // urlstack1.push(urlfileld.getText());
                    urlfield.setText(urlfield.getText());
                    jep.setPage( urlfield.getText());
                    statusbar.setText( urlfield.getText());
                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                }
                catch(IOException e)
                {
                    jep.setText("ERROR...........\n\n"+e);
                    JOptionPane.showMessageDialog(Genxplora.this,"Requ ested Page Not Found.....","ERROR",JOptionPane.ERROR_MESSAGE);
                }

            }
        });

        tool_bar.add(go);

        jep.addHyperlinkListener(new HyperlinkListener()
        {
            public void hyperlinkUpdate(HyperlinkEvent he)
            {
                if(he.getEventType()==HyperlinkEvent.EventType.ACTIVATED)
                {
                    try
                    {
                        urlstack.push(urlfield.getText());
                        // urlstack1.push(urlfileld.getText());
                        urlfield.setText(urlfield.getText());
                        jep.setPage( urlfield.getText());
                        statusbar.setText( urlfield.getText());
                        jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                    }
                    catch(IOException e)
                    {
                        jep.setText("ERROR OPENING HYPERLINK..........\n\n"+e);
                        statusbar.setText("Error Opening Hyperlink.......");
                        JOptionPane.showMessageDialog(Genxplora.this,"Requ ested Page Not Found.....","ERROR",JOptionPane.ERROR_MESSAGE);
                    }
                }
            }
        });

    }

    public static void main(String s[]) throws IOException
    {
        Genxplora tool=new Genxplora();


        tool.jep=new JEditorPane();
        tool.jep.setPreferredSize(new Dimension(790,44));
        tool.jep.setBorder(new BevelBorder(BevelBorder.LOWERED));

        tool.tool_bar.setMaximumSize(tool.tool_bar.getSize ());


        JFrame frame=new JFrame("Genxplora");


        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        frame.setJMenuBar(tool.menubar);
        frame.getContentPane().add(tool.tool_bar,BorderLayout.NORTH);
        frame.getContentPane().add(tool.jep,BorderLayout.CENTER);
        frame.getContentPane().add(tool.statusbar,BorderLayout.SOUTH);
        frame.pack();
        frame.setVisible(true);


        tool.jep.setEditable(false);

    } //end of class main




    @SuppressWarnings("serial")
    class demoaction extends AbstractAction
    {
        public demoaction(String text,Icon icon,String descri,char acc)
        {
            super(text,icon);
            putValue(ACCELERATOR_KEY,KeyStroke.getKeyStroke(acc,Toolkit.getDefaultToolkit().getMenuShortcutKeyMask()));
            putValue(SHORT_DESCRIPTION,descri);
        }

        // BackWard Button

        public void actionPerformed(ActionEvent ae)
        {
            if(ae.getActionCommand()=="Back")
            {
                if(urlstack.size()<0)
                {
                    statusbar.setText("No Page available....");
                    return;
                }

                try
                {
                    urlstack.push(urlfield.getText());
                    // urlstack1.push(urlfileld.getText());
                    urlfield.setText(urlfield.getText());
                    jep.setPage( urlfield.getText());
                    statusbar.setText( urlfield.getText());
                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                }
                catch(IOException e)
                {
                    jep.setText("ERROR......"+e);
                    JOptionPane.showMessageDialog(Genxplora.this,"Back Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                }
            }


            //Forward Button Coding

            if(ae.getActionCommand()=="Forward")
            {
                if(urlstack1.size()<0)
                {
                    statusbar.setText("No Page available...");
                    return;
                }

                try
                {
                    urlstack.push(urlstack1.pop());
                    String urlstring=(String) urlstack1.peek();
                    urlfield.setText(urlstring);
                    jep.setPage(urlstring);
                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                }
                catch(IOException e)
                {
                    jep.setText("ERROR.........\n\n"+e);
                    JOptionPane.showMessageDialog(Genxplora.this,"Forw ard Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                }
            }


            // Coding for stop

            if(ae.getActionCommand()=="Stop")
            {
                try
                {
                    urlstack.pop();
                    String str=urlstack.peek();
                    urlfield.setText(str);
                    jep.setPage(str);
                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                    statusbar.setText(str);
                }
                catch(IOException e)
                {
                    statusbar.setText("ERROR....in stopping ");
                    JOptionPane.showMessageDialog(Genxplora.this,"Stop Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                }
            } //end of stop


            //Coding of Refresh

            if(ae.getActionCommand()=="Refresh")
            {
                try
                {
                    String str=urlstack.peek();
                    urlfield.setText(str);
                    jep.setPage(str);
                    jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                    statusbar.setText("Refreshed site...."+str);
                }
                catch(IOException e)
                {
                    jep.setText("ERROR IN REFRESHING PAGE......");
                    statusbar.setText("ERROR IN REFRESHING REQUESTED PAGE......");
                    JOptionPane.showMessageDialog(Genxplora.this,"Refr esh Action not allowed.....","ERROR",JOptionPane.ERROR_MESSAGE);
                }
            }//end of refresh

        } //end of action performed

    } //end of class demoaction


    class myhandler implements ActionListener
    {
        Genxplora tool;

        public myhandler(Genxplora tool)
        {
            this.tool=tool;
        }

        public void actionPerformed(ActionEvent ae)
        {

            if(ae.getActionCommand()=="Window")
            {

                Genxplora tool1= new Genxplora();

                tool1.jep=new JEditorPane();
                tool1.jep.setPreferredSize(new Dimension(790,44));
                tool1.jep.setBorder(new BevelBorder(BevelBorder.LOWERED));

                tool1.tool_bar.setMaximumSize(tool1.tool_bar.getSize());
                JFrame frame1=new JFrame("Genxplore");


                frame1.setJMenuBar(tool1.menubar);
                frame1.getContentPane().add(tool1.tool_bar,BorderLayout.NORTH);
                frame1.getContentPane().add(tool1.jep,BorderLayout.CENTER);
                frame1.getContentPane().add(tool1.statusbar,BorderLayout.SOUTH);
                frame1.pack();
                frame1.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                frame1.setVisible(true);


                tool1.jep.setEditable(false);

            }
            if(ae.getActionCommand()=="Close")
                System.exit(0);

            //Event Handling for Open button

            if(ae.getActionCommand()=="Open...")
            {
                JFileChooser chooser=new JFileChooser();
                chooser.setMultiSelectionEnabled(true);
                int option=chooser.showOpenDialog(Genxplora.this);
                if(option==JFileChooser.APPROVE_OPTION)
                {
                    File[] sf=chooser.getSelectedFiles();
                    String flst="nothing";

                    if(sf.length > 0)
                        flst=sf[0].getName();

                    for(int i=1;i<sf.length ;++i)
                        flst+=","+sf[i].getName();

                    try
                    {
                        urlfield.setText("http://localhost/"+flst);
                        jep.setPage("http://localhost/"+flst);
                        statusbar.setText("http://localhost/"+flst);
                        jep.addHyperlinkListener(new SimpleLinkListener(jep,urlfield,statusbar));
                    }
                    catch(IOException e)
                    {
                        jep.setText("ERROR........"+e);
                        JOptionPane.showMessageDialog(Genxplora.this,"Erro r opening requested document.....","ERROR",JOptionPane.ERROR_MESSAGE);
                    }

                }
                else
                {
                    System.out.println("You Canceled");
                }
            }
            if(ae.getActionCommand()=="Save")
            {
                JFileChooser fc = new JFileChooser();
                int returnVal = fc.showSaveDialog(Genxplora.this);
                if(returnVal == JFileChooser.APPROVE_OPTION)
                {
                    String savefile = fc.getSelectedFile().getPath();
                    if(savefile == null)
                    {
                        return;
                    }
                    else
                    {
                        String docToSave = jep.getText();
                        if(docToSave != null)
                        {
                            FileOutputStream fstrm = null;
                            BufferedOutputStream ostrm = null;
                            try
                            {
                                fstrm = new FileOutputStream(savefile);
                                ostrm = new BufferedOutputStream(fstrm);
                                byte[] bytes = null;
                                try
                                {
                                    bytes = docToSave.getBytes();
                                }
                                catch(Exception e1)
                                {
                                    e1.printStackTrace();
                                }
                                ostrm.write(bytes);
                            }
                            catch(IOException io)
                            {
                                System.err.println("IOException: " +
                                        io.getMessage());
                            }
                            finally
                            {
                                try
                                {
                                    ostrm.flush();
                                    fstrm.close();
                                    ostrm.close();
                                }
                                catch(IOException ioe)
                                {
                                    System.err.println("IOException: " +
                                            ioe.getMessage());
                                }
                            }
                        }
                    }
                }
                else
                {
                    return;
                }

            }
            if(ae.getActionCommand()=="Save As...")
            {
                JFileChooser chooser=new JFileChooser();

                if(chooser.showSaveDialog(Genxplora.this)!=JFileChooser.APPROVE_OPTION)
                    return;
                File file=chooser.getSelectedFile();
                if(file==null)
                    return;
                FileWriter writer=null;
                try
                {
                    writer=new FileWriter(file);
                    textComp.write(writer);
                }
                catch(IOException e)
                {
                    JOptionPane.showMessageDialog(Genxplora.this,"File not saved","ERROR",JOptionPane.ERROR_MESSAGE);
                }
                finally
                {
                    if(writer!=null)
                        try
                    {
                            writer.close();
                    }
                    catch(IOException e)
                    {}
                }

            }

            /*if(ae.getActionCommand()=="Page Setup...")
try
{
prtMe.printDialog();
}
catch(Exception ew)
{
}*/
            if(ae.getActionCommand()=="Print...")
                try
            {
                    prtMe.printDialog();
            }
            catch(Exception ew)
            {
            }
            if(ae.getActionCommand()=="Copy")
                try
            {
                    String selection = jep.getSelectedText();
                    StringSelection clipString = new StringSelection(selection);
                    clipbd.setContents(clipString, clipString);
            }
            catch(Exception ew)
            {
            }



            if(ae.getActionCommand()=="Select All")
                try
            {
                    jep.selectAll();
            }
            catch(Exception ew)
            {
            }

            if(ae.getActionCommand()=="Find(on this page)...")
                try
            {
                    String find = "";
                    find = JOptionPane.showInputDialog(
                    "Find on this page: ");
            }
            catch(Exception ew)
            {
            }
            if(ae.getActionCommand()=="Full Screen")
            {
                tool.jep.setPreferredSize(new Dimension(900,900));

            }


            if(ae.getActionCommand()=="about browser")
            {
                JOptionPane.showMessageDialog(Genxplora.this,"Vers ion no:101bgjy1"

                        ,"ABOUT BROWSER",JOptionPane.INFORMATION_MESSAGE);
            }
        }

        public void itemStateChanged(ItemEvent ie)
        {

        }
    }



    protected JTextComponent createTextComponent()
    {
        JTextArea ta=new JTextArea();
        ta.setLineWrap(true);
        return ta;
    }


    class MyWindowAdapter extends WindowAdapter
    {
        Genxplora tool;
        public MyWindowAdapter(Genxplora tool)
        {
            this.tool=tool;
        }
        public void windowClosing(WindowEvent we)
        {

        }
    }


}




class SimpleLinkListener implements HyperlinkListener
{
    private JEditorPane pane;
    private JTextField urlfield;
    private JComboBox combox;
    private JLabel statusbar;


    public SimpleLinkListener(JEditorPane jep,JTextField jtf,JLabel j1)
    {
        pane=jep;
        urlfield=jtf;
        statusbar=j1;
    }
    public SimpleLinkListener(JEditorPane jep)
    {
        this(jep,null,null);
    }


    public void hyperlinkUpdate(HyperlinkEvent he)
    {
        HyperlinkEvent.EventType type = he.getEventType();
        if (type == HyperlinkEvent.EventType.ENTERED)
        {
            if (statusbar != null)
            {
                statusbar.setText(he.getURL().toString());
            }
        }

        else if(type == HyperlinkEvent.EventType.EXITED)
        {
            if (statusbar != null)
            {
                statusbar.setText(" ");
            }
        }
        else if(type == HyperlinkEvent.EventType.ACTIVATED)
        {
            if (he instanceof HTMLFrameHyperlinkEvent)
            {
                HTMLFrameHyperlinkEvent evt=(HTMLFrameHyperlinkEvent)he;
                HTMLDocument doc=(HTMLDocument)pane.getDocument();
                doc.processHTMLFrameHyperlinkEvent(evt);
            }
        }
        else
        {
            try
            {
                pane.setPage(he.getURL());
                if (urlfield!=null)
                {
                    urlfield.setText(he.getURL().toString());

                }
            }


            catch(FileNotFoundException e)
            {
                pane.setText("Could not open file : <tt>"+he.getURL()+"</tt>.<hr>");
            }

            catch(Exception e)
            {
                e.printStackTrace();
            }
        }
    }
} 



```

---

### Post by greenmonkeey on 2011-04-29
thanks

---

