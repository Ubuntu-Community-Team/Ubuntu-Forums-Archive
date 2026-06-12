---
title: "Guys..please help..need help executing this midlet.."
date: 2009-03-27
forum: Programming Talk
---

### Post by kriscairns on 2009-03-27
Hi guys!
I have a midlet which doesnt seem to run when deployed on my mobile phone ( N95)...Could you guys check out the program below and suggest what cold be wrong..

The midlet is supposed to start auomatically once the phone receives a SMS..and it is supposed to transfer data to a PC which it is paired with already via bluetooth...once it transfers data to the paired PC, it is supposed to receive some data and send it as SMS to a phone number defined in the code.

When I tried deploying the midlet from Netbeans, I was able to get it installed..but since it did not run automatically on receipt of SMS, I tried opening it manually on the phone..it showed an error message "Exception Handled" and gave two options..Ignore or Quit..ignore didnt work..the application opened but nothing on the screen..it was blank with the title midlet..when i tried deploying the midlet in Nokia 3600, and opened it manually..it showed a message"error-java.lang null pinter exception"..


Here goes the coding..please help guys...
there are two packages..one containing the midlet.java..and theother package containing 3 source files..serverform.java, servicelookup.java and transporter.java...

here's the midlet in one package...
----------------------------------------------------------------
[B]*receivermidlet.java:*
[/B]
package com.rva.sms.receiver;
import com.rva.blue.server.ServerForm;
import javax.microedition.io.Connector;
import javax.microedition.io.PushRegistry;
import javax.microedition.lcdui.Display;
import javax.microedition.lcdui.Displayable;
import javax.microedition.midlet.*;
import javax.wireless.messaging.Message;
import javax.wireless.messaging.MessageConnection;
import javax.wireless.messaging.TextMessage;

/**
 * @author d032602
 */
public class ReceiverMidlet extends MIDlet {
    int incomingPortNum = 6536;
    MessageConnection incomingConnection = null;
    Message incomingMessage = null;
    String inMsg;
    
    ServerForm servForm = null;

    Display display;

     /** value is true after creating the server/client */
    private boolean isInit = false;


    public void setToDisplay(Displayable previousDisp) {
        display.setCurrent(previousDisp);
    }
    public void startApp() {
        /*
        String connectList[];
        connectList = PushRegistry.listConnections(true);
        if (connectList == null || connectList.length == 0) {
            //Started by the user,exit
            destroyApp(false);
            notifyDestroyed();
        } else { //started from incoming connection...
            try {
                incomingConnection = (MessageConnection) Connector.open("sms://:" +
                        incomingPortNum);
                // Recieve the message
                incomingMessage = incomingConnection.receive();
                setIncomingMessage(incomingMessage);

                 show();

            } catch (Exception e) {
                System.out.println("IO Exception!");
            }
        }
         * */
        show();
    }

    public void pauseApp() {
    }

    public void destroyApp(boolean unconditional) {
    }

     /** Shows main menu of MIDlet on the screen. */
    public void show() {
        servForm = new ServerForm("CC station Listener", this, getIncomingMessage());
        display = Display.getDisplay(this);
        //display.vibrate(5);
        display.setCurrent(servForm);
    }

    public String getIncomingMessage() {
        return ((TextMessage) incomingMessage).getPayloadText();
    }

    public void setIncomingMessage(Message incomingMessage) {
        this.incomingMessage = incomingMessage;
    }

}

--------------------------------------------------------------
package 2:

1.***serverform.java***

package com.rva.blue.server;
 
import com.rva.sms.receiver.ReceiverMidlet;
import java.util.Enumeration;
import java.util.Vector;
import javax.bluetooth.BluetoothStateException;
import javax.bluetooth.DeviceClass;
import javax.bluetooth.DiscoveryAgent;
import javax.bluetooth.DiscoveryListener;
import javax.bluetooth.LocalDevice;
import javax.bluetooth.RemoteDevice;
import javax.bluetooth.ServiceRecord; 
import javax.microedition.lcdui.Command;
import javax.microedition.lcdui.CommandListener;
import javax.microedition.lcdui.Display;
import javax.microedition.lcdui.Displayable;
import javax.microedition.lcdui.Form;
import javax.microedition.lcdui.List;
import javax.microedition.midlet.MIDlet;

/**
 *
 * @author d032602
 */
public class ServerForm extends Form implements DiscoveryListener, Runnable, CommandListener {

    private LocalDevice localDevice = null;
    public DiscoveryAgent discAgent = null;
    private boolean isInquiring = false;
    private boolean isReady = true;
    private final String NurseAddress = "001BDC0FCDF3";
    private static Vector vecDevices = new Vector();
    private final List listScreen = new List("Devices in range", List.IMPLICIT);
    private ReceiverMidlet parent = null;
    private final Command dListBackCmd = new Command("Back", Command.BACK, 2);
    private final Command dListLoadCmd = new Command("Load", Command.OK, 1);
    private Thread thread;
    private String incomingMsg;

    public ServerForm(String title, ReceiverMidlet parent, String inMsg) {
        super(title);
        this.parent = parent;
        this.setIncomingMsg(inMsg);
        listScreen.addCommand(dListBackCmd);
        listScreen.addCommand(dListLoadCmd);
        listScreen.setCommandListener(this);
        Display.getDisplay(parent).setCurrent(this);
        thread = new Thread(this);
        thread.start();
    }

    void destroy() {
        synchronized (this) {
            notify();
        }

        // wait for acceptor thread is done
        try {
            thread.join();
        } catch (InterruptedException e) {
        } // ignore
    }

    public void deviceDiscovered(RemoteDevice btDevice, DeviceClass dClass) {
        this.isInquiring = true;
        //System.out.println("Device discovered: " + btDevice.getBluetoothAddress());
        if (!vecDevices.contains(btDevice)) {
            vecDevices.addElement(btDevice);
        }
    }

    public void servicesDiscovered(int arg0, ServiceRecord[] arg1) {
        throw new UnsupportedOperationException("Not supported yet.");
    }

    public void serviceSearchCompleted(int arg0, int arg1) {
        throw new UnsupportedOperationException("Not supported yet.");
    }

    public void inquiryCompleted(int arg0) {
        this.isInquiring = false;
        this.setTitle("Discovery completed");
        Vector btDetails = new Vector();
        String temp = null;
        RemoteDevice btDevice = null;
        for (int i = 0; i < vecDevices.size(); i++) {
            try {
                btDevice = (RemoteDevice) vecDevices.elementAt(i);
                temp = btDevice.getBluetoothAddress();
                if(temp.equals(NurseAddress)){
                    this.setTitle("Nurse add found");
                    startServiceDiscovery(btDevice);
                    return;
                }
            } catch (Exception ex) {
                System.out.println("Device details error " + ex.getMessage());
            }
        }
        if (btDetails == null) {
            this.setTitle("Restarting search");
             startDiscovery();
            //showDevices(btDetails.elements());
        }
    }

    public void run() {
        isReady = false;
        try {
            localDevice = LocalDevice.getLocalDevice();
            // get the local device
            localDevice = LocalDevice.getLocalDevice();
            // Servers set the discoverable mode to GIAC
            localDevice.setDiscoverable(DiscoveryAgent.GIAC);
            // identify the local device discovery agent
            discAgent = localDevice.getDiscoveryAgent();
            // Start discovery
            startDiscovery();
        } catch (Exception exp) {
            System.out.println("Error in run method p2: " + exp.getMessage());
            return;
        }
        isReady = true;

    }

    // To start discovery
    public void startDiscovery() {
        try {
            this.setTitle("Starting discovery");
            discAgent.startInquiry(DiscoveryAgent.GIAC, this);
            this.isInquiring = true;
        } catch (BluetoothStateException exp) {
            System.out.println("Error in starting device discovery: " + exp.getMessage());
            return;
        }
    }

     // To start service discovery
    public void startServiceDiscovery(RemoteDevice rDev) {
        this.setTitle("Searching: " + rDev.getBluetoothAddress());
        //System.out.println("Search BT services for: " + btDevice.getBluetoothAddress());
        ServiceLookup c = new ServiceLookup(rDev, this, this.getIncomingMsg());
        new Thread(c).start();
    }

    private boolean showDevices(Enumeration base) {
        Enumeration keys = base;

        // no images actually
        if (!keys.hasMoreElements()) {
            //informSearchError("No images names in found services");

            return false;
        }

        // prepare the list to be shown
        while (listScreen.size() != 0) {
            listScreen.delete(0);
        }

        while (keys.hasMoreElements()) {
            listScreen.append((String) keys.nextElement(), null);
        }
        listScreen.setCommandListener(this);
        Display.getDisplay(parent).setCurrent(listScreen);

        return true;
    }

    public void commandAction(Command c, Displayable d) {
        if (c == dListBackCmd) {
            System.out.println("Back pressed");
            Display.getDisplay(parent).setCurrent(d);
        }

    }

    public MIDlet getParent() {
        return this.parent;
    }

     public String getIncomingMsg() {
        return incomingMsg;
    }

    public void setIncomingMsg(String incomingMsg) {
        this.incomingMsg = incomingMsg;
    }
}
----------------------------------------------------------------

2.[B][I]servicelookup.java
[/I][/B]
package com.rva.blue.server;
 
import javax.bluetooth.DeviceClass;
import javax.bluetooth.DiscoveryListener;
import javax.bluetooth.RemoteDevice;
import javax.bluetooth.ServiceRecord;
import javax.bluetooth.UUID;
import javax.microedition.lcdui.Display;
import javax.microedition.lcdui.Form;
import javax.microedition.midlet.MIDlet;

/**
 *
 * @author d032602
 */
public class ServiceLookup extends Form implements DiscoveryListener, Runnable {

    private RemoteDevice btDevice = null;
    private ServerForm parent = null;
    private boolean isSearching = true;
    ServiceRecord[] records = null;
    /** The attribute id of the record item with images names. */
    private static final int NUPONS_ATTRIBUTE_ID = 0x4321;
    /** Describes this server */
    private static final UUID UUID =
            new UUID("A55665EE9F9146109085C2055C888B39", false);
    /** Optimization: keeps service search pattern. */
    private UUID[] uuidSet;
    private String incomingMsg;

    public ServiceLookup(RemoteDevice btDevice, ServerForm parent, String inMsg) {
        super("Looking up " + btDevice.getBluetoothAddress());
        this.btDevice = btDevice;
        this.parent = parent;
        this.setIncomingMsg(inMsg);
        Display.getDisplay(parent.getParent()).setCurrent(this);
    }

    public void run() {
        try {
            // initialize some optimization variables
            uuidSet = new UUID[1];
            // and only known ones, that allows pictures
            uuidSet[0] = UUID;
            // we need an only service attribute actually
            int[] attrSet = null; // default attrSet
            // Search for NuPONS Server
            this.parent.discAgent.searchServices(attrSet, uuidSet, btDevice, this);
            this.isSearching = true;
        } catch (Exception exp) {
            System.out.println("service searching run exp: " + exp.getMessage());
            return;
        }
    }

    public void deviceDiscovered(RemoteDevice arg0, DeviceClass arg1) {
    }

    public void servicesDiscovered(int arg0, ServiceRecord[] rec) {
        this.records = rec;
        String url = null;
        this.setTitle("Service Discovered");
        for (int i = 0; i < rec.length; i++) {
            url = rec[i].getConnectionURL(ServiceRecord.NOAUTHENTICATE_NOENCRYPT, false);
            if(url != null){
            Transporter trans = new Transporter(this, url, this.getIncomingMsg());
            new Thread(trans).start();
            }else{
                this.setTitle("URL is not right");
            }
        }
        this.isSearching = true;
    }

    public void serviceSearchCompleted(int arg0, int arg1) {
        this.isSearching = false;
        if (this.records == null) {
            Form f = new Form("Alert");
            f.append("Device does not support file transfer");
            Display.getDisplay(parent.getParent()).setCurrent(f);
        }
    }

    public void inquiryCompleted(int arg0) {
    }

    public MIDlet getParent() {
        return this.parent.getParent();
    }

      public String getIncomingMsg() {
        return incomingMsg;
    }

    public void setIncomingMsg(String incomingMsg) {
        this.incomingMsg = incomingMsg;
    }
}
---------------------------------------------------------------

3.[B][I]transporter.java
[/I][/B]
package com.rva.blue.server;

import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.util.Enumeration;
import java.util.Hashtable;
import javax.microedition.io.Connector;
import javax.microedition.io.StreamConnection;
import javax.microedition.lcdui.Display;
import javax.microedition.lcdui.Form;
import javax.microedition.lcdui.TextBox;  
import javax.microedition.midlet.MIDlet;
import javax.wireless.messaging.MessageConnection;
import javax.wireless.messaging.TextMessage;

/**
 *
 * @author d032602
 */
public class Transporter extends Form implements Runnable {

    String connectionURL = null;
    String Phone = "123456789";//THE MIDLET SENDS DATA TO THE //PAIRED PC AND RECEIVES DATA IN TURN AND SENDS THIS //RECEIVED //DATA TO ANOTHER PHONE AS SMS..THIS PHONE NO IS STORED IN THE //VARIABLE Phone
    StreamConnection connection = null;
    byte[] msg = "@1121".getBytes();
    private final Hashtable sendMessages = new Hashtable();
    TextBox t = new TextBox("Status", " ", 500, 0);
    ServiceLookup client;
    DataInputStream in;
    DataOutputStream out;
    private volatile boolean aborting;
    private final static byte ZERO = (byte) '0';
    private final static int LENGTH_MAX_DIGITS = 5;
    private int sendMessageId = 0;
    private String incomingMsg;

    // this is an arbitrarily chosen value:
    private final static int MAX_MESSAGE_LENGTH =
            65536 - LENGTH_MAX_DIGITS;

    public Transporter(ServiceLookup client, String connectionURL, String inMsg) {
        super("Transporter");
        this.client = client;
        this.setIncomingMsg(inMsg);
        this.connectionURL = connectionURL;        
        Display.getDisplay(client.getParent()).setCurrent(t);
    }

    public void run() {
        try {
            aborting = false;
            connection = (StreamConnection) Connector.open(connectionURL);
            t.insert("Connecting.. ", t.getCaretPosition());
            //t.insert("Transporter Opening: " + connectionURL, 0);
            out = connection.openDataOutputStream();
            in = connection.openDataInputStream();
            Integer id = new Integer(sendMessageId++);
            queueMessageForSending(id, msg);
            // start the writer
            Writer writer = new Writer(this);
            Thread writeThread = new Thread(writer);
            writeThread.start();
            while (!aborting) {
                int length = 0;
                t.insert("-Waiting to read ", t.getCaretPosition());
                try {                    
                    byte[] lengthBuf = new byte[LENGTH_MAX_DIGITS];
                    readFully(in, lengthBuf);
                    length = readLength(lengthBuf);
                    byte[] temp = new byte[length];
                    readFully(in, temp);
                    if(temp != null){
                        aborting = true;
                        sendSMS(new String(temp), Phone);

                    }                    
                } catch (IOException e) {
                    close();
                }
            }
            // Closing the connections and terminating the midlet
            //aborting=false;
            //close();
            //client.getParent().notifyDestroyed();
        } catch (IOException e) {
            t.insert("-Transporter Err: " + e.getMessage(), t.getCaretPosition());
        }
    }

    private static int readLength(byte[] buffer) {
        int value = 0;
        for (int i = 0; i < LENGTH_MAX_DIGITS; ++i) {
            value *= 10;
            value += buffer[i] - ZERO;
        }
        return value;
    }

    private static void readFully(InputStream in, byte[] buffer) throws IOException {
        int bytesRead = 0;

        while (bytesRead < buffer.length) {
            int count = in.read(buffer,
                    bytesRead,
                    buffer.length - bytesRead);
            if (count == -1) {
                throw new IOException("Input stream closed");
            }
            bytesRead += count;
        }
    }

    public void queueMessageForSending(Integer id, byte[] data) {
        synchronized (sendMessages) {
            sendMessages.put(id, data);
            sendMessages.notify();
        }
    }

    private void sendMessage(OutputStream out, byte[] data)
            throws IOException {

        byte[] buf = new byte[LENGTH_MAX_DIGITS + data.length];
        writeLength(data.length, buf);
        System.arraycopy(data,
                0,
                buf,
                LENGTH_MAX_DIGITS,
                data.length);
        out.write(buf);
        out.flush();
        t.insert("-Data Flushed: " + msg.toString(), t.getCaretPosition());
    }

    public void sendSMS(String data, String number) {
        try {
             t.insert("-Sending: " + data, t.getCaretPosition());
            String addr1 = "sms://" + number;
            MessageConnection conn = (MessageConnection) Connector.open(addr1);
            t.insert("-Opening sms conn", t.getCaretPosition());
            TextMessage tmsg =
                (TextMessage)conn.newMessage(MessageConnection.TEXT_MESSAGE);
            tmsg.setPayloadText(data);
            conn.send(tmsg);
        } catch (Exception e) {
            t.insert("/SMS Err: " + e.getMessage(), t.getCaretPosition());
        }
    }

    private static void writeLength(int value, byte[] buffer) {
        for (int i = LENGTH_MAX_DIGITS - 1; i >= 0; --i) {
            buffer[i] = (byte) (ZERO + value % 10);
            value = value / 10;
        }
    }

    public void close() {
        if (!aborting) {
            synchronized (this) {
                aborting = true;
            }

            synchronized (sendMessages) {
                sendMessages.notify();
            }

            if (out != null) {
                try {
                    out.close();
                    synchronized (this) {
                        out = null;
                    }
                } catch (IOException e) {
                    // there is nothing we can do: ignore it
                }
            }

            if (in != null) {
                try {
                    in.close();
                    synchronized (this) {
                        in = null;
                    }
                } catch (IOException e) {
                    // there is nothing we can do: ignore it
                }
            }

            if (connection != null) {
                try {
                    connection.close();
                    synchronized (this) {
                        connection = null;
                    }
                } catch (IOException e) {
                    // there is nothing we can do: ignore it
                }
            }
        }
    }

    public MIDlet getParent() {
        return this.client.getParent();
    }

    public String getIncomingMsg() {
        return incomingMsg;
    }

    public void setIncomingMsg(String incomingMsg) {
        this.incomingMsg = incomingMsg;
    }

    private class Writer
            implements Runnable {

        private final Transporter handler;

        Writer(Transporter handler) {
            this.handler = handler;
        }

        public void run() {
            while (!aborting) {
                synchronized (sendMessages) {
                    Enumeration e = sendMessages.keys();
                    if (e.hasMoreElements()) {
                        // send any pending messages
                        Integer id = (Integer) e.nextElement();
                        byte[] sendData =
                                (byte[]) sendMessages.get(id);
                        try {
                            sendMessage(out, sendData);

                            // remove sent message from queue
                            sendMessages.remove(id);
                        } catch (Exception ex) {
                            close(); // stop the networking thread 
                        }
                    }

                    if (sendMessages.isEmpty()) {
                        try {
                            sendMessages.wait();
                        } catch (InterruptedException ex) {
                            // this can't happen in MIDP: ignore it
                        }
                    }
                }
            }
        }
    }
}

----------------------------------------------------------------
thats it guys...the 2 packages together form one project..and i need to get it working..any ideas guys..please help...thanks in advance..

---

### Post by nvteighen on 2009-03-27
Hell... use the [ CODE ] [ /CODE ] tags... please! (without spaces)

---

### Post by s.fox on 2009-03-27
Yes, plus it keeps it all nicely indented.

---

