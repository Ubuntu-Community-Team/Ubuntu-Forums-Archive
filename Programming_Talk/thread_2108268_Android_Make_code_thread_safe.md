---
title: "Android: Make code thread safe?"
date: 2013-01-24
forum: Programming Talk
---

### Post by fallenshadow on 2013-01-24
Hey all,

Recently I discovered that an Android app I developed that worked perfectly in the emulator does not work on a phone for many of the more complex activities. :shock:

I did read a little about something called thread safe. I want to know more about it, like how would I adjust my existing code to make it thread safe?

Anyone have experience with it?

---

### Post by ofnuts on 2013-01-24
> **fallenshadow said:**
> Hey all,

Recently I discovered that an Android app I developed that worked perfectly in the emulator does not work on a phone for many of the more complex activities. :shock:

I did read a little about something called thread safe. I want to know more about it, like how would I adjust my existing code to make it thread safe?

Anyone have experience with it?
Start here: [http://en.wikipedia.org/wiki/Thread_safety](http://en.wikipedia.org/wiki/Thread_safety)

But your code is multi-threaded only if you explicitly start threads. Is this the case? Your problem could be elsewhere.

---

### Post by fallenshadow on 2013-01-25
My code doesn't start new threads or anything. Hmm... ive no idea what is going on then. I thought if it runs fine on the emulator that it is 100% gonna work on a phone. :/

```

package com.my.app;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.MalformedURLException;
import java.net.ProtocolException;
import java.net.URL;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;

import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.Node;
import org.w3c.dom.NodeList;

import android.app.Activity;
import android.content.Context;
import android.content.Intent;
import android.net.ConnectivityManager;
import android.os.Bundle;
import android.os.Environment;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class CurrencyActivity extends Activity {
	
	private Button convertBtn;
	private Double SEKrate;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.curr_layout);
		
		convertBtn=(Button)findViewById(R.id.convertBtn);
		convertBtn.setOnClickListener(convertBtnClick);
		
		
		if(checkInternetConnection()==true)
		{
			LoadDataWeb();
		}
		else if(checkInternetConnection()==false)
		{
			//read the offline file
			System.out.println("No internet connection.");
			String Path = Environment.getExternalStorageDirectory().getPath() + "/CURR/curr.xml";
			File f = new File(Path);
			
			if(f.exists())
			{
				LoadData();
			}
			else
			{
				Intent intent = new Intent(getApplicationContext(), NoInternet.class);
				intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
				startActivity(intent);
			}
		}
	}
	
	public Double getSEKrate() {
		return SEKrate;
	}

	public void setSEKrate(Double sEKrate) {
		SEKrate = sEKrate;
	}
	
	private OnClickListener convertBtnClick=new OnClickListener(){

		public void onClick(View v) {
			convertCurrency();
		}
		
	};
	
	public boolean checkInternetConnection() {

		ConnectivityManager conMgr = (ConnectivityManager) getSystemService (Context.CONNECTIVITY_SERVICE);

		if (conMgr.getActiveNetworkInfo() != null && conMgr.getActiveNetworkInfo().isAvailable() && conMgr.getActiveNetworkInfo().isConnected()) {
			return true;
		} 
		else {
			return false;
		}

	}

	public void LoadDataWeb() {
		
		//update file and read
		System.out.println("We have internet connection.");
		
		  HttpURLConnection connection = null;
	      BufferedReader rd  = null;
	      StringBuilder sb = null;
	      String line = null;
	    
	      URL serverAddress = null;
	    
	      try {
	          serverAddress = new URL("http://www.ecb.int/stats/eurofxref/eurofxref-daily.xml");
	          //set up out communications stuff
	          connection = null;
	        
	          //Set up the initial connection
	          connection = (HttpURLConnection)serverAddress.openConnection();
	          connection.setRequestMethod("GET");
	          connection.setDoOutput(true);
	          connection.setReadTimeout(10000);
	                    
	          connection.connect();
	        
	          //read the result from the server
	          rd  = new BufferedReader(new InputStreamReader(connection.getInputStream()));
	          sb = new StringBuilder();
	        
	          while ((line = rd.readLine()) != null)
	          {
	              sb.append(line + '\n');
	          }
	        
	          System.out.println(sb.toString());
	          
	          String state = Environment.getExternalStorageState();
	          System.out.println(state);
	          
	          if(state.equals("mounted"))
	          {
	        	  String Path = Environment.getExternalStorageDirectory().getPath() + "/CURR/curr.xml";
				  File f = new File(Path);
				  System.out.println(Path);
				  
				  f.createNewFile();
				  FileOutputStream fOut = new FileOutputStream(f);
			      OutputStreamWriter myOutWriter = new OutputStreamWriter(fOut);
			      myOutWriter.append(sb.toString());
				  myOutWriter.close();
				  fOut.close();
				  
				  System.out.println("File written to " + Path);
				  
				  if(f.exists())
				  {
					  LoadData();
				  }
	          }
	                    
	      } catch (MalformedURLException e) {
	          e.printStackTrace();
	      } catch (ProtocolException e) {
	          e.printStackTrace();
	      } catch (IOException e) {
	          e.printStackTrace();
	      }
	      finally
	      {
	          //close the connection, set all objects to null
	          connection.disconnect();
	          rd = null;
	          sb = null;
	          connection = null;
	      }
		
	}
	
	public void LoadData() {

			 try {
				 
				    String Path = Environment.getExternalStorageDirectory().getPath() + "/CURR/curr.xml";
					File fXmlFile = new File(Path);
					DocumentBuilderFactory dbFactory = DocumentBuilderFactory.newInstance();
					DocumentBuilder dBuilder = dbFactory.newDocumentBuilder();
					Document doc = dBuilder.parse(fXmlFile);
					doc.getDocumentElement().normalize();
			 
					System.out.println("Root element :" + doc.getDocumentElement().getNodeName());
					NodeList nList = doc.getElementsByTagName("Cube");
			 
					for (int temp = 0; temp < nList.getLength(); temp++) {
			 
					   Node nNode = nList.item(temp);
					   if (nNode.getNodeType() == Node.ELEMENT_NODE) {
			 
					      Element eElement = (Element) nNode;
					      
					      if(temp==1)
					      {
					    	  String date = eElement.getAttribute("time");
						      System.out.println("DATE : " + date);
					      }
					      if(temp==13)
					      {
					    	  String curr = eElement.getAttribute("currency");
					    	  System.out.println("CURRENCY:" + curr);
					    	  String rate = eElement.getAttribute("rate");
					    	  System.out.println("RATE:" + rate);
					    	  Double SEKrate = Double.parseDouble(rate);
					    	  this.setSEKrate(SEKrate);
					      }
					   }
					}
					
				  } catch (Exception e) {
					e.printStackTrace();
				  }
	}
	
	public void convertCurrency() {
		EditText editText = (EditText)findViewById(R.id.amountBox);

		String editTextStr = editText.getText().toString();
		Double inputNum = Double.parseDouble(editTextStr);
		 
		Double result = inputNum*SEKrate;
		
		TextView text = (TextView) findViewById(R.id.result);
		text.setText(String.format("%.2f", result));
		
	}
	
}


```

I hate bombarding you with all my code but in your free time could you take a look?

---

### Post by r-senior on 2013-01-25
Can you access the logs on the device to see if there are any exceptions thrown?

---

### Post by ofnuts on 2013-01-25
> **fallenshadow said:**
> My code doesn't start new threads or anything. Hmm... ive no idea what is going on then. I thought if it runs fine on the emulator that it is 100% gonna work on a phone. :/

```

package com.my.app;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.MalformedURLException;
import java.net.ProtocolException;
import java.net.URL;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;

import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.Node;
import org.w3c.dom.NodeList;

import android.app.Activity;
import android.content.Context;
import android.content.Intent;
import android.net.ConnectivityManager;
import android.os.Bundle;
import android.os.Environment;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class CurrencyActivity extends Activity {
    
    private Button convertBtn;
    private Double SEKrate;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.curr_layout);
        
        convertBtn=(Button)findViewById(R.id.convertBtn);
        convertBtn.setOnClickListener(convertBtnClick);
        
        
        if(checkInternetConnection()==true)
        {
            LoadDataWeb();
        }
        else if(checkInternetConnection()==false)
        {
            //read the offline file
            System.out.println("No internet connection.");
            String Path = Environment.getExternalStorageDirectory().getPath() + "/CURR/curr.xml";
            File f = new File(Path);
            
            if(f.exists())
            {
                LoadData();
            }
            else
            {
                Intent intent = new Intent(getApplicationContext(), NoInternet.class);
                intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
                startActivity(intent);
            }
        }
    }
    
    public Double getSEKrate() {
        return SEKrate;
    }

    public void setSEKrate(Double sEKrate) {
        SEKrate = sEKrate;
    }
    
    private OnClickListener convertBtnClick=new OnClickListener(){

        public void onClick(View v) {
            convertCurrency();
        }
        
    };
    
    public boolean checkInternetConnection() {

        ConnectivityManager conMgr = (ConnectivityManager) getSystemService (Context.CONNECTIVITY_SERVICE);

        if (conMgr.getActiveNetworkInfo() != null && conMgr.getActiveNetworkInfo().isAvailable() && conMgr.getActiveNetworkInfo().isConnected()) {
            return true;
        } 
        else {
            return false;
        }

    }

    public void LoadDataWeb() {
        
        //update file and read
        System.out.println("We have internet connection.");
        
          HttpURLConnection connection = null;
          BufferedReader rd  = null;
          StringBuilder sb = null;
          String line = null;
        
          URL serverAddress = null;
        
          try {
              serverAddress = new URL("http://www.ecb.int/stats/eurofxref/eurofxref-daily.xml");
              //set up out communications stuff
              connection = null;
            
              //Set up the initial connection
              connection = (HttpURLConnection)serverAddress.openConnection();
              connection.setRequestMethod("GET");
              connection.setDoOutput(true);
              connection.setReadTimeout(10000);
                        
              connection.connect();
            
              //read the result from the server
              rd  = new BufferedReader(new InputStreamReader(connection.getInputStream()));
              sb = new StringBuilder();
            
              while ((line = rd.readLine()) != null)
              {
                  sb.append(line + '\n');
              }
            
              System.out.println(sb.toString());
              
              String state = Environment.getExternalStorageState();
              System.out.println(state);
              
              if(state.equals("mounted"))
              {
                  String Path = Environment.getExternalStorageDirectory().getPath() + "/CURR/curr.xml";
                  File f = new File(Path);
                  System.out.println(Path);
                  
                  f.createNewFile();
                  FileOutputStream fOut = new FileOutputStream(f);
                  OutputStreamWriter myOutWriter = new OutputStreamWriter(fOut);
                  myOutWriter.append(sb.toString());
                  myOutWriter.close();
                  fOut.close();
                  
                  System.out.println("File written to " + Path);
                  
                  if(f.exists())
                  {
                      LoadData();
                  }
              }
                        
          } catch (MalformedURLException e) {
              e.printStackTrace();
          } catch (ProtocolException e) {
              e.printStackTrace();
          } catch (IOException e) {
              e.printStackTrace();
          }
          finally
          {
              //close the connection, set all objects to null
              connection.disconnect();
              rd = null;
              sb = null;
              connection = null;
          }
        
    }
    
    public void LoadData() {

             try {
                 
                    String Path = Environment.getExternalStorageDirectory().getPath() + "/CURR/curr.xml";
                    File fXmlFile = new File(Path);
                    DocumentBuilderFactory dbFactory = DocumentBuilderFactory.newInstance();
                    DocumentBuilder dBuilder = dbFactory.newDocumentBuilder();
                    Document doc = dBuilder.parse(fXmlFile);
                    doc.getDocumentElement().normalize();
             
                    System.out.println("Root element :" + doc.getDocumentElement().getNodeName());
                    NodeList nList = doc.getElementsByTagName("Cube");
             
                    for (int temp = 0; temp < nList.getLength(); temp++) {
             
                       Node nNode = nList.item(temp);
                       if (nNode.getNodeType() == Node.ELEMENT_NODE) {
             
                          Element eElement = (Element) nNode;
                          
                          if(temp==1)
                          {
                              String date = eElement.getAttribute("time");
                              System.out.println("DATE : " + date);
                          }
                          if(temp==13)
                          {
                              String curr = eElement.getAttribute("currency");
                              System.out.println("CURRENCY:" + curr);
                              String rate = eElement.getAttribute("rate");
                              System.out.println("RATE:" + rate);
                              Double SEKrate = Double.parseDouble(rate);
                              this.setSEKrate(SEKrate);
                          }
                       }
                    }
                    
                  } catch (Exception e) {
                    e.printStackTrace();
                  }
    }
    
    public void convertCurrency() {
        EditText editText = (EditText)findViewById(R.id.amountBox);

        String editTextStr = editText.getText().toString();
        Double inputNum = Double.parseDouble(editTextStr);
         
        Double result = inputNum*SEKrate;
        
        TextView text = (TextView) findViewById(R.id.result);
        text.setText(String.format("%.2f", result));
        
    }
    
}


```I hate bombarding you with all my code but in your free time could you take a look?

Not an expert in Android UIs, but the surprising with you code isn't that it's not thread safe... is that it seems it is not using threads when it should... as far as I can tell you are starting an Internet connection with an HTTP request in the  UI thread, so any delays in the response hang the UI.

See [http://stackoverflow.com/questions/6179449/android-threaded-httpclient-task-without-blocking-ui](http://stackoverflow.com/questions/6179449/android-threaded-httpclient-task-without-blocking-ui)

---

### Post by fallenshadow on 2013-01-25
Yes I did have some idea that I would need to use Asynctask.

The problematic line according to the phone error log is this:

```
connection.connect();
```

As far as I know Async task takes 3 parameters. 

1. The parameter sent to the task for doInBackground().
2. The parameter for onProgressUpdate().
3. The parameter for the onPostExecute() result.

My question is, what parameters should I use for my code?

Here is what I think it should be thus far:

1. URL.
2. Integer.
3. ?? - not sure.

---

### Post by KdotJ on 2013-01-25
I've not really read your code, but as general information you can use Void as a parameter type.

```
AsyncTask<URL, Integer, Void>
```

---

### Post by fallenshadow on 2013-01-25
Yeah I was thinking maybe void might be my best option.

I will work on implementing the Asynctask tomorrow and see how it goes. :)

Thanks to everyone who chipped in advice to help me!

---

