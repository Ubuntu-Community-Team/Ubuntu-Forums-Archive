---
title: "[Java]Problem"
date: 2009-12-28
forum: Programming Talk
---

### Post by SpinningAround on 2009-12-28
I'm having some problem with these two code parts, in the first part can't be compiled since plotTraffic is non-static and part of the inner class Draw. paintDiagram is a non-static method in Draw. 

In the other part will trigger when 'START' is clicked after that will the GUI window will lock up, I guess because the program never return from actionPerformed.

Question is what is needed to be done to get it working?

```

	private static void active(long trafficLimit){
		while(todayTraffic<=trafficLimit){
			Wait.oneSec();
			if(runScript()!=null){
				todayTraffic = Long.parseLong(runScript());
				trafficAmount.setText("" + todayTraffic + " of " + trafficLimit);
				plotTraffic.paintDiagram();
			}
			else{
				break;
			}
		}
		closeOperation();
	}


```


```

	public void actionPerformed(ActionEvent event){
		Object obj = event.getSource();
		if(obj instanceof JButton){
			String info = event.getActionCommand();
			int tal = Integer.parseInt(info);
			switch(tal){
				case 10:	trafficInput.setEditable(false);
							if(trafficInput.getText()!=null){
								try{
									trafficLimit=(Long.parseLong(trafficInput.getText()))*1000000000;
									//convert the info in trafficInput from GB to byte
									errorMSG.setText(""); //new try reset error message
									
									active(trafficLimit);
									}
								}

```

---

### Post by doas777 on 2009-12-28
in your active block, is plotTraffic a object or a class/type?

for static's invoke it as 'Type.StaticMethod()'
for non-statics create an instance with new, and call your method. 
```
plotTraffic pt = new plotTraffic(); 
pt.paintDiagram()
```

---

### Post by Some Penguin on 2009-12-29
> **SpinningAround said:**
> I'm having some problem with these two code parts, in the first part can't be compiled since plotTraffic is non-static and part of the inner class Draw. paintDiagram is a non-static method in Draw. 

In the other part will trigger when 'START' is clicked after that will the GUI window will lock up, I guess because the program never return from actionPerformed.

Question is what is needed to be done to get it working?

```

    private static void active(long trafficLimit){
        while(todayTraffic<=trafficLimit){
            Wait.oneSec();
            if(runScript()!=null){
                todayTraffic = Long.parseLong(runScript());
                trafficAmount.setText("" + todayTraffic + " of " + trafficLimit);
                plotTraffic.paintDiagram();
            }
            else{
                break;
            }
        }
        closeOperation();
    }


```

Well, you can't access non-static members from a static method.  Is there a reason that's a static method?   And if so, which plotTraffic do you expect it to use?  You need to figure out what you want to do:

1) make it non-static, and use the plotTraffic that presumably is a member of the instance
2) keep it static, and pass the plotTraffic as a parameter
3) keep it static, and make plotTraffic a static member
4) keep it static, and make plotTraffic a singleton, and invoke the getter

There's a good chance that three of those four won't make any sense for your application.


```

    public void actionPerformed(ActionEvent event){
        Object obj = event.getSource();
        if(obj instanceof JButton){
            String info = event.getActionCommand();
            int tal = Integer.parseInt(info);
            switch(tal){
                case 10:    trafficInput.setEditable(false);
                            if(trafficInput.getText()!=null){
                                try{
                                    trafficLimit=(Long.parseLong(trafficInput.getText()))*1000000000;
                                    //convert the info in trafficInput from GB to byte
                                    errorMSG.setText(""); //new try reset error message
                                    
                                    active(trafficLimit);
                                    }
                                }

```


The second code block looks to be very truncated.  If you think it's not terminating, either use a debugger to examine the stack while it runs, or add some logging messages so you know which method calls it's executing.

---

