---
title: "Read Remote File"
date: 2009-08-14
forum: Programming Talk
---

### Post by mthalis on 2009-08-14
I want read remote machine file using Java in windows environment(can be Linux to windows or other way around). 
note - that remote machine don't have server(Apache or other)

---

### Post by mthalis on 2009-08-14
I find way to read file in ftp server

```

import java.net.*;
import java.io.*;

public class FileSender {

    public static void main(String args[]) {
        String nextLine;
        URL url = null;
        URLConnection urlConn = null;
        InputStreamReader inStream = null;
        BufferedReader buff = null;
        try {
            //String uri = "sftp://" + user + ":" + password + "@" + host
            //+ "/" + remotePath;
            //String uri = "ftp://ites:123456@192.168.101.28/home/ites/Documents/text.html";
            String uri = "ftp://192.168.101.100/README";
            // Create the URL obect that points
            // at the default file index.html
            url = new URL(uri);
            urlConn = url.openConnection();
            inStream = new InputStreamReader(
                    urlConn.getInputStream());
            buff = new BufferedReader(inStream);

            // Read and print the lines from index.html
            while (true) {
                nextLine = buff.readLine();
                if (nextLine != null) {
                    System.out.println(nextLine);
                } else {
                    break;
                }
            }
        } catch (MalformedURLException e) {
            System.out.println("Please check the URL:" +
                    e.toString());
        } catch (IOException e1) {
            System.out.println("Can't read  from the Internet: " +
                    e1.toString());
        }
    }
}

```

Now **I want to read image and display it JFrame**  any idea?

---

### Post by mthalis on 2009-08-17
Any Suggestion?

---

### Post by mthalis on 2009-08-17
I used this code it satisfy my requirement, I want to comments about this coding, Is it good or bad

```

import java.net.MalformedURLException;
import java.net.URL;
import java.util.logging.Level;
import java.util.logging.Logger;


public class test extends javax.swing.JFrame {

    public test() {
        a = new javax.swing.JLabel();
        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        try {
            //a.setIcon(new javax.swing.ImageIcon("/home/ites/Videos/1.jpg"));
            //a.setIcon(new javax.swing.ImageIcon(new URL("http://www.anddev.org/images/tiny_tutheaders/weather_forecast.png")));
            a.setIcon(new javax.swing.ImageIcon(new URL("http://192.168.101.30/1.jpg")));
        } catch (MalformedURLException ex) {
            Logger.getLogger(test.class.getName()).log(Level.SEVERE, null, ex);
        }
        add(a);
        pack();
    }

    public static void main(String args[]) {
        java.awt.EventQueue.invokeLater(new Runnable() {

            public void run() {
                new test().setVisible(true);
            }
        });
    }
    private javax.swing.JLabel a;
}

```

---

