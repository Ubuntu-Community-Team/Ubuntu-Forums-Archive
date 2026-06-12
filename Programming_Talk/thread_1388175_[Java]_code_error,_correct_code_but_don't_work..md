---
title: "[Java] code error, correct code but don't work."
date: 2010-01-22
forum: Programming Talk
---

### Post by SpinningAround on 2010-01-22
There is something wrong in my code but I can't figure out what it's, first error or logical error is when I try to read a stream from a bash script (script work) for some unknown reason will it end up in the System.out.println(ERROR:...). Second problem is that setVar won't work in the active() method, yet when I try it in main(...) does it work. setVar(boolean,double,String)

Stream Error:
[PHP]
	private static long runScript(String scriptPath, boolean destroy, boolean stream){
		long resultat=-1;
		try{
			Process process = Runtime.getRuntime().exec(scriptPath);
			process.waitFor();
			
			if(stream){
				BufferedReader inputStreamReader  = new BufferedReader(new InputStreamReader(process.getInputStream()));
				BufferedReader errStreamReader  = new BufferedReader(new InputStreamReader(process.getErrorStream()));

				StringBuffer output = new StringBuffer();
				StringBuffer error = new StringBuffer();
			
				for(String line;(line=inputStreamReader.readLine())!=null;)
				{
					output.append(line);
				}
				for(String line;(line=errStreamReader.readLine())!=null;)
				{
					error.append(line);
				}
				if( error.toString()!="" ){
					System.out.println("ERROR:|" + error.toString() + "|"); //edit
					process.destroy();
					return -1;
				}
				resultat = Long.parseLong( output.toString() ); //catch error
			}
			else{
				resultat = process.exitValue();
			}
			
			if(destroy){
				process.destroy();
			}
			return resultat;
		}
		catch (InterruptedException e){
			e.printStackTrace();
		}
		catch (IOException e){
			e.printStackTrace();
		}
		return -1;
	}
[/PHP]

**setvar() in active() ** don't work
[PHP]
		long todayTraffic=0;
		double procent;
		try{
				Thread.currentThread().sleep(1000);
				todayTraffic=runScript(TRAFFICCHECK,true,true);
				if(todayTraffic!=-1){
					if( (limitTraffic>0) && (todayTraffic>=limitTraffic) ){
						closeOperation();
					}
				}
				else{
					closeOperation();
				}
				procent = ( (double)todayTraffic/(double)limitTraffic )*100;
				System.out.println("" + currentStatus +" "+ procent +" "+ reportTraffic(todayTraffic) ); //looks fine
				monitor.setVar( currentStatus , procent , reportTraffic(todayTraffic) );
			}
			closeOperation();
		}
[/PHP]

**varSet(): in main(..)** Works
[PHP]
		window = new SettingsGraphic();
		monitor = new ActiveGraphic();
		double a=0;
		long c = 1000;
		boolean b=true;
		while(true){
			for(int i=0;i<90;i++){
				a=a+0.01;
				c=c+108431258;
				monitor.setVar(b,a,reportTraffic(c));
				if(b){
					b=false;
				}
				else{
					b=true;
				}
			Thread.currentThread().sleep(1000);
		}
		a=0;
		}
[/PHP]

EDIT:
setVar();
[PHP]
	private JLabel infoTraffic,status;
	private boolean active;
	private double procent;

	public void setVar(boolean active, double procent,String traffic){
		this.active=active;
		this.procent=procent;
		infoTraffic.setText("Traffic : " + traffic);
		repaint();
	}
[/PHP]

I have added these lines to active(), but with no difference
[PHP]
		NumberFormat form = new DecimalFormat("#.##");
		form = NumberFormat.getInstance(Locale.US);
				procent = Double.parseDouble( form.format( ( (double)todayTraffic/(double)limitTraffic )*100 ) );
[/PHP]

---

### Post by Axos on 2010-01-22
One problem is with this line:

```

if( error.toString()!="" ){

```

That compares references, not the contents of the strings. To compare the contents of the strings, you need to change the line to this:

```

if (!error.toString().equals("")) {

```

Or, more efficiently, you can just check the length of the StringBuffer:

```

if (error.length() != 0) {

```

To help you with your setVar problem, I need a lot more detail. EDIT: I see you edited your post while I was composing mine. I will look at your update to see if I can figure it out.

---

### Post by Axos on 2010-01-22
OK, about setVar, please explain what's not working. Is the text on the window not being updated?

In a GUI program (whether it's Java Swing or any other GUI programming environment), your code should not sleep when called on the event dispatching thread. That messes up all kinds of things, including the user's ability to click on buttons, etc. Your code should be event-driven. Take a look at javax.swing.Timer:

[http://java.sun.com/javase/6/docs/api/javax/swing/Timer.html](http://java.sun.com/javase/6/docs/api/javax/swing/Timer.html)

---

### Post by SpinningAround on 2010-01-23
Your first post fixed the error problem, regarding the second so does it look like setVar() never execute the repaint() part. If I let active() make the window visible with monitor.show() will I simply get a gray window with a title. I tested having the working test version that trigger setVar() running and as soon as active() did start did the monitor window stop refreshing. My program is something like this 
[ main --(create)--> (Settings Window) ---> (start clicked in Settings) ---> ( start active() ) ---> active() start sending info to setVar() for monitor to repaint. ]

new ActiveGraphic(); <--- Monitor ---> new SettingsGraphic();

       

Settings GUI
[PHP]
	public void actionPerformed(ActionEvent event){
		if(event.getSource() instanceof JButton){
			JButton result = (JButton)event.getSource();
			String temp = result.getText();
			boolean done = true;
			if(temp=="START"){
				if(done){
					Monitor.execute();
				}
[/PHP]
Monitor.execute();
[PHP]
	public static void execute() {
		settings.dispose(); 
		active(limitTraffic);
	}
[/PHP]

---

### Post by Axos on 2010-01-23
You cannot do anything time-consuming (whether doing a large amount of computation, blocking on I/O, or simply sleeping) on the event dispatch thread. Each time Swing lets you know an event has occurred (like a button click), you need to do a little work and then return back to Swing (which means returning from the method which Swing called) as soon as possible (ideally in less than a second). If you need to do something once a second, you need to use [javax.swing.Timer]("http://java.sun.com/javase/6/docs/api/javax/swing/Timer.html"). So when the user clicks the Start button, you should create a Timer to call active() once a second. Remove the call to sleep() in active(). When active() is called, it will do its job once and then return. Then one second later it will be called again. When you want this to stop, disable the Timer.

I hope I'm explaining this clearly. If not, I can write a very small program that does something simple like display the current time, updating it every second.

In a program which needs to do something very time consuming (like a long computation or a large amount of I/O or any I/O which can possibly block), you need to look into using [javax.swing.SwingWorker](http://java.sun.com/javase/6/docs/api/javax/swing/SwingWorker.html) to create a separate thread to do the time-consuming stuff. But don't forget that you cannot call any Swing methods from code called on that thread (or any other thread besides the event dispatch thread). You have to communicate any results back to the event dispatch thread in order to display them in the GUI.

---

