---
title: "Problems with Asynchronous calls between GSOAP C++ server and AXIS Java client"
date: 2008-12-29
forum: Programming Talk
---

### Post by rajeesh_11 on 2008-12-29
Hi,

I trying to run a Axis JAVA client with a GSOAP C++ server. Here in the below given code I am trying to make an asynchronous call from the JAVA client using "sendReceiveNonBlocking" API. On the GSOAP server side I am using the "soap_send_..." for the asynchronous behaviour. 

I have a callback pointer on the JAVA client "MyAxisCallback" which will wait for asynchronous reponse from the GSOAP server. But this approach is not working. The client sends a string to server which is received successfully by the server. After that the callback pointer then keeps on waiting for a response from the server. The client calls the "ns2__hello" function on the server and the server has to send a response using the "soap_send_ns2__hello" function to the JAVA callback pointer. But the callback pointer doesn’t receive anything, it just keeps on waiting till the server times out. 

The same GSOAP C++ server works fine with a GSOAP C++ client for asynchronous calls.

What could be the problem here ?? Any inputs will be appreciated…

Thanks and Regards,
Rajeesh


The Server code

// This is the main project file for VC++ application project 
// generated using an Application Wizard.

#include <soapH.h>
#include < math.h > // for sqrt() 
#include "ns2.nsmap"
#include <stdafx.h>
//#include <AsynchOp.h>
//#include <unistd.h>

#define BACKLOG (100) // Max. request backlog
#using <mscorlib.dll>
#include <soapProxy.h>
#include "cmythread.h"
#include "cmythread1.h"
using namespace System;

int _tmain()
{
  


   struct soap soap;
   int m, s; // master and slave sockets

   soap_init2(&soap, SOAP_IO_KEEPALIVE, SOAP_IO_KEEPALIVE);
    soap.send_timeout = 6000; // 60 seconds
	soap.recv_timeout = 6000; // 60 seconds
	soap.accept_timeout = 3600; // server stops after 1 hour of inactivity
	soap.max_keep_alive = 1000; // max keep-alive sequence
	void *process_request(void*);
	struct soap *tsoap;
	//pthread tid;
   //soap_init(&soap);
   //m = soap_bind(&soap, "http://10.143.73.103/", 80, 100);
   m = soap_bind(&soap, NULL,80, 100);
   if (m < 0)
   {std::cout<<"already inside "<<std::endl;
   soap_print_fault(&soap, stderr);}
   else
   {
      fprintf(stderr, "Socket connection successful: master socket = %d\n", m);
	  CMyThread	thread;
//	  CMyThread1 thread1;


      for (int i = 1; ; i++)
      {
         s = soap_accept(&soap);
		 if (!soap_valid_socket(s))
		 {
			 if (soap.errnum)
			 { 
				 soap_print_fault(&soap, stderr);
				 exit(1);
			 }
			 fprintf(stderr, "server timed out\n");
           break;
		 }
		 fprintf(stderr, "Thread %d accepts socket %d connection from IP %d.%d.%d.%d\n",i, s, (soap.ip>>24)&0xFF, (soap.ip>>16)&0xFF, (soap.ip>>8)&0xFF, soap.ip&0xFF);
		 /*tsoap = soap_copy(&soap);
		 if (!tsoap)
		 break;*/
		 
		 thread.soap1= soap_copy(&soap);
		 if (!thread.soap1)
		 break;
		 std::cout<< " Entering create thread "<< std::endl;
		 bool ab=thread.CreateThread ();
		 if(!ab)
		 {
			 std::cout<<"ok"<<std::endl;
		 }
	     //Sleep (20);
		// pthread create(&tid, NULL, (void*(*)(void*))process request, (void*)tsoap);
	  }
   } 
std::cout<<"will release callback"<<std::endl;
soap_done(&soap);
return 0;
   
}

unsigned long CMyThread1::Process (void* parameter)
{
 return 0;  
}
unsigned long CMyThread::Process (void* parameter)
{

	//a mechanism for terminating thread should be implemented
	//not allowing the method to be run from the main thread
	if (::GetCurrentThreadId () == this->hMainThreadId)
	{  std::cout<<"Error main thraed"<<std::endl;
		return 0;
	}
	else {

		std::cout<<"start soap_serve((struct soap*)soap1)"<<std::endl;
		//::MessageBoxW (0, _T("I'm running in a different thread!"), _T("CMyThread"), MB_OK);
		soap_serve((struct soap*)soap1);

		std::cout<<"end soap_serve((struct soap*)soap1)"<<std::endl;
		soap_destroy((struct soap*)soap1); // dealloc C++ data
		soap_end((struct soap*)soap1); // dealloc data and clean up
		return 0;

	}

}
   
int ns2__add(struct soap *soap, int a)
{ 

std::cout<<"inside add"<<std::endl;
std::cout<<"a is"<<a<<std::endl;
a = a+8;
soap_send_ns2__add(soap,NULL, NULL,a); 

std::cout<<"after send"<<std::endl;
return SOAP_OK;
}

int ns2__hello(struct soap *soap, char *s) 
{ 
  std::cout<<"inside hello -- "<<s<<std::endl;
  s = "Hello World!"; 
  if (soap_send_ns2__hello(soap,NULL, NULL,s))
  {
	  std::cout<<"error -- "<<std::endl;
	  return soap->error;
  }
  return SOAP_OK; 
}


The Client Code

package impl;

import java.util.HashMap;

import javax.xml.stream.XMLStreamException;

import org.apache.axiom.om.OMAbstractFactory;
import org.apache.axiom.om.OMElement;
import org.apache.axiom.om.OMFactory;
import org.apache.axiom.om.OMNamespace;
import org.apache.axiom.om.impl.llom.util.AXIOMUtil;
import org.apache.axis2.AxisFault;
import org.apache.axis2.addressing.EndpointReference;
import org.apache.axis2.client.Options;
import org.apache.axis2.client.ServiceClient;
import org.apache.axis2.client.async.AsyncResult;
import org.apache.axis2.client.async.AxisCallback;
import org.apache.axis2.client.async.Callback;
import org.apache.axis2.context.MessageContext;
import org.apache.xmlbeans.impl.soap.SOAPEnvelope;
import org.tempuri.ns2_xsd.service_wsdl.ServiceStub;


public class Sync
{
   // private static String toEPR = "http://10.143.73.103:80";
    private static EndpointReference targetEPR = new EndpointReference("http://10.143.73.103:80");
    
    /*static AxisCallback axisCallback = new AxisCallback() 
    {
		public void onMessage(MessageContext arg0) {
			// TODO Auto-generated method stub
			System.out.println("got message");
			synchronized(this){
				this.notify();
			}
		}

		public void onFault(MessageContext arg0) {
			// TODO Auto-generated method stub
			System.out.println("Got fault");
			synchronized(this){
				this.notify();
			}
		}

		public void onError(Exception arg0) {
			// TODO Auto-generated method stub
			System.out.println("on error" + arg0);
			synchronized(this){
				this.notify();
			}
		}

		public void onComplete() {
			// TODO Auto-generated method stub
			System.out.println("complete");
			synchronized(this){
				this.notify();
			}
		}
		   
	   };*/
    
    public static void main(String[] args) 
	{
        
//    	 First create the payload of the message.
    	System.out.println("in main");
    	//OMElement payload = getPayload(); // add your payload here
    	OMElement payload =createPayLoad();

//    	 Create an instance of service client.
    	ServiceClient serviceClient;
    	
		try {
			serviceClient = new ServiceClient();
		
			//ServiceStub s ;
			
//    	 Create an options object to pass parameters to service client.
    	Options options = new Options();
    	            
//    	 Set the location of the Web service.
    	options.setTo(targetEPR);
    	options.setAction("ns2:hello");

    	serviceClient.setOptions(options);
    	            
//    	 Create a callback object.
    	//MyCallback callback = new MyCallback();
    	MyAxisCallback axisCallback = new MyAxisCallback();
    	/*try {
			Thread.sleep(5000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}*/
//    	 Do an async invocation.
    	//serviceClient.sendReceiveNonBlocking(payload, callback);
    	serviceClient.sendReceiveNonBlocking(payload,axisCallback);

    	/*try {
			Thread.sleep(5000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}*/
		
		while (!axisCallback.isComplete())
		{
			Thread.sleep(1000);
			System.out.println("Not yet completed!!");
		}
		MessageContext mCont = serviceClient.getLastOperationContext().getMessageContext("Out");
		System.out.println(mCont.getEnvelope().getFirstElement().getText());
		
		System.out.println("Callback completed!!");
		 /*while (!callback.isComplete()) {

		      Thread.sleep(1000);
		      
		      System.out.println("axisCallback.isComplete()" + callback.isComplete());

		    }*/
	
		 //System.out.println("axisCallback.isComplete()" + callback.toString());
		
    	System.out.println("after non blocking call"); 
		} catch (AxisFault e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

//    	 Continue doing other work without waiting until the response comes.
    	
	}    
    
    public static OMElement getPayload(){
    	int a = 2;

		OMFactory fac = OMAbstractFactory.getOMFactory();
		OMNamespace omNs = fac.createOMNamespace(
		                  "http://tempuri.org/ns2.xsd", "ns2");
		OMElement method = fac.createOMElement("hello", omNs);
		OMElement value = fac.createOMElement("value", omNs);
		//value.setText("Hello , my first service utilization");
		method.addChild(value);
		//value.setText(Integer.toString(a));
		value.setText("hello India");
		System.out.println("value is"+ value);
		System.out.println("method is"+ method);
		 return method;
    	//return payload;
		//return 
    }
    public static OMElement createPayLoad() {

        OMFactory fac = OMAbstractFactory.getOMFactory();
        OMNamespace omNs = fac.createOMNamespace(
                "http://tempuri.org/ns2.xsd", "ns2");
        OMElement method = fac.createOMElement("hello", omNs);
        OMElement value = fac.createOMElement("value", omNs);
        method.addChild(value);
         value.setText("hello India");
        return method;
    }
}
    
class MyCallback extends Callback {

	  public void onComplete(AsyncResult result) {
	     // Get the response SOAP envelope from the result.
	     //SOAPEnvelope envelope = result.getResponseEnvelope();
	            
	     // Process SOAP envelope.
		  System.out.println("Inside OnComplete");
	   }

	   public void onError(Exception e) {
	     // Write here what you want to do in case of an error.
		   System.out.println("Inside OnError"); 
	   }		
}

class MyAxisCallback implements AxisCallback {

	private boolean bComplete;
	public void onMessage(MessageContext arg0) {
		// TODO Auto-generated method stub
		String happy = arg0.getEnvelope().getFirstElement().getText();
		System.out.println("Inside onMessage" + happy);
	}

	public void onFault(MessageContext arg0) {
		// TODO Auto-generated method stub
		String nothappy = arg0.getEnvelope().getFirstElement().getText();
		System.out.println("Inside onFault" + nothappy);
	}

	public void onError(Exception arg0) {
		// TODO Auto-generated method stub
		System.out.println("Inside onError");
		bComplete = true;
		arg0.printStackTrace();
	}

	public void onComplete() {
		// TODO Auto-generated method stub
		bComplete = true;
		System.out.println("Inside onComplete");
	}
	
	public boolean isComplete() {
		return bComplete;
	}
}

---

### Post by rajeesh_11 on 2008-12-31
I am still stuck up with this problem. A simple "sendReceive" call from the Axis Client is also hanging. I have attached the java client file with this reply....if someone knows something about this problem please reply soon...as I said before this GSOAP server is working fine with a GSOAP client....and the Axis Java client can send the payload(data) to GSOAP server using "sendReceive" or "sendReceiveNonBlocking" but the receiving of the data for the client is not happening.....the "sendRecieve" call hangs and the callback pointer for "sendReceiveNonBlocking" doesnt receive anything...

---

