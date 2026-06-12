---
title: "need help with progress bar in Java"
date: 2009-04-18
forum: Programming Talk
---

### Post by Mia_tech on 2009-04-18
guys, I'm trying to get working a progress bar for my "IP Scanner" app (netbeans project), the progress bar I set it to go off when I press the "start" button and the frame shows up, but not the progress bar itself <attached file> the complete progress bar shows up once the task is completed "that's no fun"... also I inserted the "progressBar1.setValue(i);" in the for(loop) that scans for IP's so it gets the update to the bar, but that's not working either... guys what am I missing here?.... HELP!

progress bar method

```
public JProgressBar progressBar1;
    public JFrame frame;
    private void buttonStartIPscanActionPerformed(java.awt.event.ActionEvent evt) {                                                  
        /**
         * progress bar displaying ip scan
         */
        frame = new JFrame("IP Scanner");
        Container content = frame.getContentPane();
        JButton cancel = new JButton("Cancel");
        cancel.setSize(50, 25);
        content.add(cancel);
        progressBar1 = new JProgressBar();
        progressBar1.setMinimum(0);
        progressBar1.setMaximum(block.size());
        progressBar1.setStringPainted(true);
        Border border = BorderFactory.createTitledBorder("Scanning...");
        progressBar1.setBorder(border);
        content.add(progressBar1, BorderLayout.NORTH);
        frame.setSize(300, 100);
        frame.setVisible(true);
 }  
```

IP Scan method

```
IPrange netRange = new IPrange();
    ArrayList<String> block = netRange.getRange();
    /**
     * performing ip scan
     */
    @Action
    public void StartIPscan()
    {
        String ipFrom = txtboxIPfrom.getText();
        String ipTo = txtboxIPto.getText();
        netRange.setFromip(ipFrom);
        netRange.setToip(ipTo);
        netRange.StrToIP();
        netRange.calcNetwork();
        /**
         * ping sweep network
         */
        boolean ping = false;
        String ipadd = "";
        ipadd = "Scanning network "+"\""+block.get(0)+"\""+"...."+"\n";
        txtareaIPscan.setText(ipadd);
        for(int i = 0; i < block.size(); i++)
        {
            try
            {
                int timeout = 1500;
                InetAddress address = InetAddress.getByName(block.get(i));
                ping = address.isReachable(timeout);
                progressBar1.setValue(i);//updating progress bar
                if(ping == true)
                {
                     ipadd = block.get(i)+" is alive!"+"\n";
                     txtareaIPscan.append(ipadd);
                }
            }
            catch(IOException e)
            {
                System.out.println(e);
            }
        }
    }  
```

---

### Post by The Cog on 2009-04-18
I think you have trapped the thread that would normally deal with repainting the GUI in your scanning loop. So it doesn't get back to repaint the progress bar until the scan is finished, by which time it's 100% of course.

I would be inclined to have the start scan button start a different thread to run the scan. Suns java tutorial has a whole section on doing things like this. I can't remember the details and it may have changed a bit since I last looked at making a java GUI so I can't offer good details I'm afraid. But I'm sure the issue is that you are capturing the GUI maintenance thread for the duration of the scan.

Here is a starting point:
[http://java.sun.com/docs/books/tutorial/uiswing/concurrency/index.html](http://java.sun.com/docs/books/tutorial/uiswing/concurrency/index.html)

---

