---
title: "Java/.Net Voice recording"
date: 2006-04-24
forum: Programming Talk
---

### Post by Venki_scott on 2006-04-24
can any one help me out to solve my exception which arosed whenever i try to run the .net application(C# using ikvm dll,a java file runs well independently).. Basically the java program to record the sound/voice and to playback... here is the code 
import java.io.*;
import javax.sound.sampled.*;

public class JavaToNet23 implements Runnable{

  boolean stopCapture = false;
  public ByteArrayOutputStream byteArrayOutputStream;
  public AudioFormat audioFormat;
  public TargetDataLine targetDataLine;
  public AudioInputStream audioInputStream;
  public SourceDataLine sourceDataLine;
  public static boolean l_boolRecord=true; 
  byte tempBuffer[] = new byte[10000];
  

  public static void main(String args[]){
    new JavaToNet23();
  }

  public JavaToNet23(){//constructor
      }//end constructor

  //This method captures audio input from a
  // microphone and saves it in a
  // ByteArrayOutputStream object.
  public void captureAudio(){
  	l_boolRecord=true;
    try{
      //Get and display a list of
      // available mixers.
      Mixer.Info[] mixerInfo = 
                      AudioSystem.getMixerInfo();
      System.out.println("Available mixers:");
      for(int cnt = 0; cnt < mixerInfo.length;
                                          cnt++){
      	System.out.println(mixerInfo[cnt].
      	                              getName());
      }//end for loop

      //Get everything set up for capture
      audioFormat = getAudioFormat();

      DataLine.Info dataLineInfo =
                            new DataLine.Info(
                            TargetDataLine.class,
                            audioFormat);

      //Select one of the available
      // mixers.
      Mixer mixer = AudioSystem.
                          getMixer(mixerInfo[3]);
      
      //Get a TargetDataLine on the selected
      // mixer.
      targetDataLine = (TargetDataLine)
                     mixer.getLine(dataLineInfo);
      //Prepare the line for use.
      targetDataLine.open(audioFormat);
      targetDataLine.start();

      Thread th=new Thread(this,"Start Thread");
      th.start();
    } catch (Exception e) {
      System.out.println(e);
      
    }//end catch
  }//end captureAudio method
  public void stopRecord(){
	stopCapture=false;
  }
  //This method plays back the audio data that
  // has been saved in the ByteArrayOutputStream
  public void playAudio() {
  	l_boolRecord=false;
    try{
      //Get everything set up for playback.
      //Get the previously-saved data into a byte
      // array object.
    	System.out.println("HISHIHSIHISHISHI   "+byteArrayOutputStream);
      byte audioData[] = byteArrayOutputStream.
                                   toByteArray();
      //Get an input stream on the byte array
      // containing the data
      InputStream byteArrayInputStream =
             new ByteArrayInputStream(audioData);
      AudioFormat audioFormat = getAudioFormat();
      audioInputStream = new AudioInputStream(
                    byteArrayInputStream,
                    audioFormat,
                    audioData.length/audioFormat.
                                 getFrameSize());
      DataLine.Info dataLineInfo = 
                            new DataLine.Info(
                            SourceDataLine.class,
                            audioFormat);
      sourceDataLine = (SourceDataLine)
               AudioSystem.getLine(dataLineInfo);
      sourceDataLine.open(audioFormat);
      sourceDataLine.start();

      //Create a thread to play back the data and
      // start it  running.  It will run until
      // all the data has been played back.
      Thread th=new Thread(this,"Start Thread");
      th.start();
    } catch (Exception e) {
      System.out.println(e);
      
    }//end catch
  }//end playAudio

  //This method creates and returns an
  // AudioFormat object for a given set of format
  // parameters.  If these parameters don't work
  // well for you, try some of the other
  // allowable parameter values, which are shown
  // in comments following the declartions.
  private AudioFormat getAudioFormat(){
    float sampleRate = 8000.0F;
    //8000,11025,16000,22050,44100
    int sampleSizeInBits = 16;
    //8,16
    int channels = 1;
    //1,2
    boolean signed = true;
    //true,false
    boolean bigEndian = false;
    //true,false
    return new AudioFormat(
                      sampleRate,
                      sampleSizeInBits,
                      channels,
                      signed,
                      bigEndian);
  }//end getAudioFormat
//=============================================//

/* (non-Javadoc)
 * @see java.lang.Runnable#run()
 */
public void run() {
 	if(l_boolRecord){
 	    byteArrayOutputStream =
 	                     new ByteArrayOutputStream();
 	    stopCapture = false;
 	    try{//Loop until stopCapture is set by
 	        // another thread that services the Stop
 	        // button.
 	      while(!stopCapture){
 	        //Read data from the internal buffer of
 	        // the data line.
 	        int cnt = targetDataLine.read(tempBuffer,
 	                              0,
 	                              tempBuffer.length);
 	        if(cnt > 0){
 	          //Save data in output stream object.
 	          byteArrayOutputStream.write(tempBuffer,
 	                                      0,
 	                                      cnt);
 	        }//end if
 	      }//end while
 	      byteArrayOutputStream.close();
 	    }catch (Exception e) {
 	      System.out.println(e);
 	    }//end catch
 	  	}else{
 	  		 try{
 	  	      int cnt;
 	  	      //Keep looping until the input read method
 	  	      // returns -1 for empty stream.
 	  	      while((cnt = audioInputStream.read(
 	  	      	              tempBuffer, 0,
 	  	                      tempBuffer.length)) != -1){
 	  	        if(cnt > 0){
 	  	          //Write data to the internal buffer of
 	  	          // the data line where it will be
 	  	          // delivered to the speaker.
 	  	          sourceDataLine.write(tempBuffer,0,cnt);
 	  	        }//end if
 	  	      }//end while
 	  	      //Block and wait for internal buffer of the
 	  	      // data line to empty.
 	  	      sourceDataLine.drain();
 	  	      sourceDataLine.close();
 	  	    }catch (Exception e) {
 	  	      System.out.println(e);
 	  	    }//end catch
 	  	}
	
}


}
My C#  code is 
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;

namespace WindowsApplication10
{
	/// <summary>
	/// Summary description for Form1.
	/// </summary>
	public class Form1 : System.Windows.Forms.Form
	{
		private System.Windows.Forms.Button button1;
		private System.Windows.Forms.Button button2;
		private System.Windows.Forms.Button button3;
		public JavaToNet23 ki;
		/// <summary>
		/// Required designer variable.
		/// </summary>
		private System.ComponentModel.Container components = null;

		public Form1()
		{
			//
			// Required for Windows Form Designer support
			//
			InitializeComponent();

			//
			// TODO: Add any constructor code after InitializeComponent call
			//
		}

		/// <summary>
		/// Clean up any resources being used.
		/// </summary>
		protected override void Dispose( bool disposing )
		{
			if( disposing )
			{
				if (components != null) 
				{
					components.Dispose();
				}
			}
			base.Dispose( disposing );
		}

		#region Windows Form Designer generated code
		/// <summary>
		/// Required method for Designer support - do not modify
		/// the contents of this method with the code editor.
		/// </summary>
		private void InitializeComponent()
		{
			this.button1 = new System.Windows.Forms.Button();
			this.button2 = new System.Windows.Forms.Button();
			this.button3 = new System.Windows.Forms.Button();
			this.SuspendLayout();
			// 
			// button1
			// 
			this.button1.Location = new System.Drawing.Point(128, 112);
			this.button1.Name = "button1";
			this.button1.Size = new System.Drawing.Size(128, 24);
			this.button1.TabIndex = 0;
			this.button1.Text = "Record";
			this.button1.Click += new System.EventHandler(this.button1_Click);
			// 
			// button2
			// 
			this.button2.Location = new System.Drawing.Point(120, 160);
			this.button2.Name = "button2";
			this.button2.Size = new System.Drawing.Size(144, 24);
			this.button2.TabIndex = 1;
			this.button2.Text = "Stop";
			this.button2.Click += new System.EventHandler(this.button2_Click);
			// 
			// button3
			// 
			this.button3.Location = new System.Drawing.Point(136, 208);
			this.button3.Name = "button3";
			this.button3.Size = new System.Drawing.Size(120, 24);
			this.button3.TabIndex = 2;
			this.button3.Text = "Play";
			this.button3.Click += new System.EventHandler(this.button3_Click);
			// 
			// Form1
			// 
			this.AutoScaleBaseSize = new System.Drawing.Size(5, 13);
			this.ClientSize = new System.Drawing.Size(292, 266);
			this.Controls.Add(this.button3);
			this.Controls.Add(this.button2);
			this.Controls.Add(this.button1);
			this.Name = "Form1";
			this.Text = "Form1";
			this.Load += new System.EventHandler(this.Form1_Load);
			this.ResumeLayout(false);

		}
		#endregion

		/// <summary>
		/// The main entry point for the application.
		/// </summary>
		[STAThread]
		static void Main() 
		{
			Application.Run(new Form1());
		}

		private void button1_Click(object sender, System.EventArgs e)
		{
			ki.captureAudio();
			Console.WriteLine("Hi Venki ..."+ki.byteArrayOutputStream.toString());



		}

		private void button2_Click(object sender, System.EventArgs e)
		{
			Console.WriteLine("Hi Venki Stop ..."+ki.byteArrayOutputStream.toString());
			ki.stopRecord();
			Console.WriteLine("Hi Venki Stop ..."+ki.byteArrayOutputStream.toString());
		}

		private void button3_Click(object sender, System.EventArgs e)
		{
			Console.WriteLine("Hi Venki Play  ..."+ki.byteArrayOutputStream.toString());
			ki.playAudio();
			Console.WriteLine("Hi Venki PLay ..."+ki.byteArrayOutputStream.toString());
			
		}

		private void Form1_Load(object sender, System.EventArgs e)
		{
		ki=new JavaToNet23();
		}

		
	}
}

this the excpetion 

"An unhandled exception of type 'System.NullReferenceException' occurred in WindowsApplication10.exe"

---

