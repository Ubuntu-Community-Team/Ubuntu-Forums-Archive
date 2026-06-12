---
title: "command line args how access method"
date: 2015-01-27
forum: Programming Talk
---

### Post by vijay9 on 2015-01-27
how to access this method through command line argument with scanner class
when i press 1 call first method so on to 5
```
 static void callMenu(){
         for(int i = 1; i<=5;i++) {
         switch(i) {
             case 1:
                 menu.Balance();
                 break;
             case 2:
                 menu.CashWithDraw();
                 break;
             case 3:
                 menu.MiniStatement();
                 break;
             case 4:
                 menu.ChangePin();
                 break;
             case 5:
                 menu.Exit();
                 break;
             default:
                 System.out.println("please press only given button");
         }
       }
    }&#65279;
```

---

### Post by Vy0m on 2015-01-27
Not sure what are you trying to achieve, but to pass arguments to your program you have to specify it in the function call.

The loop you used there would just loop from 1 to 5 and call each function in a sequence. Is that what you intent to do?

---

### Post by vijay9 on 2015-01-28
now i change the format and its working
static void callMenu(int a){
      // int val1;
       // val1 = Integer.parseInt(val.nextLine());
         switch(a) {
             case 1:
                 menu.Balance();
                 break;
             case 2:
                 menu.CashWithDraw();
                 break;
             case 3:
                 menu.MiniStatement();
                 break;
             case 4:
                 menu.ChangePin();
                 break;
             case 5:
                 menu.Exit();
                 break;
             default:
                 System.out.println("please press only given button");
         }
       //}
    }

============================================

public static void main(String args[]) {
      ATMLogin log = new ATMLogin();
      scnr a = new scnr();
      
      System.out.println("Enter Your AcNo:");
      ATMLogin.a1 = a.sc.next();
      
      System.out.println("Enter Your Pin");
      ATMLogin.a2 = a.sc.next();
      
      AccsLogin.CompareLogIn();
      
      //menu a3 = new menu();  
      System.out.println("WelCome To SBI ATM");
     int a4 = a.sc.nextInt();
      atm.login.menu.callMenu(a4);
     // a3.callMenu(a.sc.a4);
     
  }

---

