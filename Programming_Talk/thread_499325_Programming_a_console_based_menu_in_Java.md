---
title: "Programming a console based menu in Java"
date: 2007-07-12
forum: Programming Talk
---

### Post by rhipwell on 2007-07-12
Hi everyone, i am having a small problem - I cant seem to get the following code to iterate properly. 

```
      System.out.println("Please Make a selection:"); 
        System.out.println("[1] Add a new record"); 
        System.out.println("[2] Open an existing record"); 
        System.out.println("[3] exit"); 
        
        System.out.println("Selection: "); 
        int selection=scanner.nextInt();     
       
       switch (selection){
             
           case 1:System.out.println("Adding new record");
                break;
             
        
           case 2:System.out.println("Opening existing record");
                break;
             
        
           case 3:System.out.println("Exit Successful");
                System.exit(0);
                        
           default:System.out.println("Please enter a valid selection.");
           
       };
        
        
        return selection;
    }
```

What happens the way the code is currently writen is the program ends when any character is pushed. What I want to have happen is if anything other then 1,2 or 3 is pressed, the program displays the menu again awaiting letigiment input. 

I have tried do...while loops and empty for loops (relying on break statements) and in every circumstance I end up with an infinite loop once any character outside of the case statements is pressed. 

Any thoughts? Thanks

-Rob

---

### Post by blueEbola on 2007-07-12
Hi,

You need some sort of loop.  What did your loop code look like before?  I'd imagine that something like this would work (my java's a bit rusty, but hopefully you understand it):

```


while (1) {

       System.out.println("Please Make a selection:"); 
        System.out.println("[1] Add a new record"); 
        System.out.println("[2] Open an existing record"); 
        System.out.println("[3] exit"); 
        
        System.out.println("Selection: "); 
        int selection=scanner.nextInt();     
       
        if (selection == 3) {
        // exit if selection = 3
                break;
        }

       switch (selection){
             
           case 1:System.out.println("Adding new record");
                break;
             
        
           case 2:System.out.println("Opening existing record");
                break;
                                     
           default:System.out.println("Please enter a valid selection.");
           
       };
}

```

---

### Post by rhipwell on 2007-07-12
Thanks for the reply BlueEbola. The code you provided put me on the right track. Here is the code that works for me. Thanks again

```

        public static int MainMenu(){
      //Displays the main menu and handles passing off to next menu. 
     
        Scanner scanner = new Scanner (System.in);
        int selection=0;
        int x=0;
        
        while(x==0){   //changed while(1) to a value that didn't complain in netbeans
            System.out.println("Please Make a selection:"); 
            System.out.println("[1] Add a new record"); 
            System.out.println("[2] Open an existing record"); 
            System.out.println("[3] exit"); 
            System.out.println("Selection: "); 
            selection=scanner.nextInt();     
        
       switch (selection){
             
           case 1:System.out.println("Adding new record");
                x=1;
                break;
             
        
           case 2:System.out.println("Opening existing record");
                x=1;
                break;
             
        
           case 3:System.out.println("Exit Successful");
                System.exit(0);
                        
           default:System.out.println("Please enter a valid selection.");
           
            };
        
        }  
        return selection;
    }

```

Thanks Again

-Rob

---

### Post by jespdj on 2007-07-13
> while(x==0){   //changed while(1) to a value that didn't complain in netbeans

Just write this:

```
while (true) {
```

---

### Post by Ramses de Norre on 2007-07-13
> **jespdj said:**
> Just write this:

```
while (true) {
```

He changes the value of x to get out of the  while loop, which is impossible when you use while(true).

---

