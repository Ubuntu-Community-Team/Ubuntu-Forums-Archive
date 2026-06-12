---
title: "browser in java (Project)"
date: 2011-04-18
forum: Programming Talk
---

### Post by greenmonkeey on 2011-04-18
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

public class genxplora extends JPanel 
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
   
```


hi guys this is my java   Project..but the problem in this code is when i run this project,only few things are working on the toolbar...how can i make them work..do let me know the code...help will be appreciated...

---

### Post by Sub101 on 2011-04-18
Is there a problem?

---

### Post by greenmonkeey on 2011-04-18
ya only few things are working on the toolbar..i want to code for the other options as well given in the toolbar.so i am looking for the solution...:):confused:

---

### Post by simeon87 on 2011-04-18
> **greenmonkeey said:**
> ya only few things are working on the toolbar..i want to code for the other options as well given in the toolbar.so i am looking for the solution...:):confused:

Ok, but if you want us to help you should be more specific. We're not going to read all the code and figure out what you want. So, what are the missing options and what exactly do you need help with? The general idea of how it works or a specific problem in your current implementation?

---

### Post by greenmonkeey on 2011-04-18
okay to be more specific in my toolbar there are no option of back,refresh,forward,stop that are present in the standard browser..so i just want to add those to my browser?? okay sir??

---

### Post by greenmonkeey on 2011-04-18
u must have seen the back and forward button in the browser,so i want the same button in my browser which can be seen...

---

### Post by greenmonkeey on 2011-04-18
hey dude do u need more explanation...would u help me pls...i hv explained you as u said....

---

### Post by Sub101 on 2011-04-18
To clarify;

You need to know how to add buttons for the functions of: Refresh, Back and Forward to the toolbar along the top of the screen?

---

### Post by greenmonkeey on 2011-04-18
yes  u got it right...let me know pls?

---

### Post by Sub101 on 2011-04-18
Having had a quick look through, it looks like you havent set the Action Command. Therefore the button listeners are checking for the ActionCommand which is not set.

What you may have intended to use was the "getSource()" method.

---

### Post by greenmonkeey on 2011-04-18
can u tell me where to use this method...make changes in my program and paste it pls

---

### Post by magneze on 2011-04-18
Will you credit him when you hand this in? ;)

---

### Post by Sub101 on 2011-04-18
> **greenmonkeey said:**
> can u tell me where to use this method...make changes in my program and paste it pls

Is this your own code?

It seems to me to be of fairly good quality, in which case you shouldnt have a problem fixing the errors.

---

### Post by greenmonkeey on 2011-04-18
no its not my own code..i m doing this for my love...ishe told me to run this code..although there are some errors in it i rectified them bt still she asked to put buttons on it like i told u in earlier post....pls guys help me...:):confused:

---

### Post by simeon87 on 2011-04-18
> **greenmonkeey said:**
> no its not my own code..i m doing this for my love...ishe told me to run this code..although there are some errors in it i rectified them bt still she asked to put buttons on it like i told u in earlier post....pls guys help me...:):confused:

So an important lesson is: only do things for your love that you're actually capable of. I don't want to be harsh but [last time]("http://ubuntuforums.org/showthread.php?t=1726406") you were unable to fix a problem when the error message told you what to do.

Do you want to learn Java or do you want us to solve your problems? This whole thread shows no effort from you to even attempt to understand what you're dealing with. Do some reading on building GUI applications in Java and adding buttons shouldn't be too hard.. the real challenge comes from making it a working web browser.

---

### Post by cgroza on 2011-04-18
Take a look at your toolbar object API's, look for a tutorial for your GUI toolkit. I am sure that you can find one that teaches you how to create a toolbar because in is a pretty basic thing.

Put some heart in it.

---

