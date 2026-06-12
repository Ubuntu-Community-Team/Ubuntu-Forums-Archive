---
title: "ClassCastException while running my Xlet which extends a Thinlet in OpenMHP"
date: 2007-10-01
forum: Programming Talk
---

### Post by sachinparadkar on 2007-10-01
Hi,
I am running a Java program which runs fine when I run it as a standalone application but when I try to integrate it in OpenMHP ,which is the real requirement,it gives me a ClassCastException. Here is my code . 


/*
 * ICueApp.java
 * 
 * Created on Sep 26, 2007, 12:18:34 AM
 * 
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package com.itaas.icue;

import java.awt.Color;
import java.awt.Font;
import java.awt.Graphics;
import java.awt.event.KeyEvent;
import java.io.IOException;
import thinlet.FrameLauncher;
import thinlet.Thinlet;
import javax.tv.xlet.*;

/**
 *
 * @author 
 */
public class ICueApp extends Thinlet implements javax.tv.xlet.Xlet{
    private static final Class[] ICueApp = null;

	Object m_RootPanel ;

	private XletContext context;
	
    public ICueApp() throws XletStateChangeException,ClassCastException {
    		System.out.println("Inside the Constructor for ICueApp");
    		initXlet(context);
    		
    		//System.out.println("context -->" + context);
        	setFont(new Font("SansSerif", Font.PLAIN, 11));
		try {
                    m_RootPanel = parse("EventData.xml");
	            add(m_RootPanel);
		} catch (Exception exc) { exc.printStackTrace(); }
	}

	public static void main(String[] args) throws Exception {
		new FrameLauncher(null,new ICueApp(), 400, 100); // 208x235
	}
    
	/*public static void main(String args[]) {
		SIManager manager = SIManager.createInstance();
		SIEmulator emulator = SIEmulator.getInstance();
		System.out.println("emulator" + emulator);
		emulator.putXlet(0, "ICueApp", "ICueApp", null);
	}*/
	
    public void closeDialog(Object dialog) {
		remove(dialog);
	}

    public void exit()
    {
        System.exit(0);
    }
    
    public void showDialog(String name) throws IOException,ClassCastException 
    {
        System.out.println("Inside the showDialog method" + name);
    	add(parse(name + ".xml"));
    }
    
   
	public void initXlet(XletContext ctx) throws XletStateChangeException,ClassCastException {
		System.out.println("Inside the initXlet method");
		//this.context = ctx;


		try {
			System.out.println("Before calling the EventData.xml method");
			String name = "EventData";
			//System.out.println("ctx " + ctx + " name " + name);
			showDialog(name);
			System.out.println("After calling the EventData.xml method");
		} catch (IOException e) {
			// TODO Auto-generated catch block
			System.out.println("Exception " + e);
			e.printStackTrace();
		} 

	}

	public void keyPressed (KeyEvent key) {
		if (key.getKeyCode()==KeyEvent.VK_ENTER) {
			try {
				destroyXlet(true);
			} catch (XletStateChangeException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
	
	public void keyTyped(KeyEvent ignored) {   }

	public void keyReleased(KeyEvent ignored) {   }

	public void destroyXlet(boolean unconditional) throws XletStateChangeException {
		// TODO Auto-generated method stub
		
	}

	public void pauseXlet() {
		// TODO Auto-generated method stub
		
	}

	public void startXlet() throws XletStateChangeException,ClassCastException {
		// TODO Auto-generated method stub
	//	validate();
		
	}





}

---

### Post by amira on 2008-02-18
Hi,
I need your help, could you provide me with a copy of the openMHP code? I tried to download it from openmhp.org but it seems that the site is browken. 
thanks

---

