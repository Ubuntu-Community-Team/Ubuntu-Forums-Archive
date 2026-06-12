---
title: "need help with progress bar in Java"
date: 2009-04-16
forum: Programming Talk
---

### Post by Mia_tech on 2009-04-16
guys, I'm trying to implement a progress bar as part of my ip scanner app which is suppose to display once the user press the "start" button, but I'm running into a couple of problems
1) the progress bar is displaying once the process has finished scanning all the ips, instead of doing it while scanning the ips
2) how could I get the progress from the task and feed it into the progress bar for displaying of the progress
3) also the progress bar is showing in the top left corner of the screen... how could I put it right infront of the application

here's the @action of the "start" button

[PHP]@Action
    public void StartIPscan()
    {
        String ipFrom = txtboxIPfrom.getText();
        String ipTo = txtboxIPto.getText();
        netRange.setFromip(ipFrom);
        netRange.setToip(ipTo);
        netRange.StrToIP();
        netRange.calcNetwork();
        String ipScan = netRange.pingSweep();
        /**
         * progress bar displaying ip scan
         */
        JFrame f = new JFrame("IP Scanner");
        Container content = f.getContentPane();
        JProgressBar progressBar1 = new JProgressBar();
        progressBar1.setValue(0);
        progressBar1.setStringPainted(true);
        Border border = BorderFactory.createTitledBorder("Scanning...");
        progressBar1.setBorder(border);
        content.add(progressBar1, BorderLayout.NORTH);
        f.setSize(300, 100);
        f.setVisible(true);
        txtareaIPscan.setText(ipScan);
    }[/PHP]

---

