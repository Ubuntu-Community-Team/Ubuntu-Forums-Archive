---
title: "Segmentation fault (core dump)"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by kerapu on 2014-05-19
hello everyone.....im new to ubuntu, i have this coding but when i run it it show segmentation fault (core dump)....please help me to solve it....

~sory about the language~

Coding:

```
#include <newt.h>#include <stdlib.h>#include <stdio.h>#include <string.h>void location(char *);void time(char *);char* fullC;int main (int argc, char * argv[]){char input1[20];location(input1);time(input1);return 0;}void location( char *input1C){char intro[] = "\t\t\tPLEASE SELECT YOUR CURRENT BUS STATION!!";newtComponent form1,label1,bOK,bCancel,listbox,teks1;const void *selection;newtInit();newtCls();//newtPushHelpLine(NULL);teks1 = newtTextboxReflowed(1,1,intro,50, 3,3,0);newtCenteredWindow(60,20,"EFFICIENT BUS SYSTEM");bOK = newtButton (20,15, "OK");bCancel = newtButton (30,15, "CANCEL");form1 = newtForm(NULL, NULL, 0);listbox= newtListbox(1,4,10, NEWT_FLAG_SCROLL | NEWT_FLAG_BORDER);newtListboxAppendEntry(listbox, "SERUMPUN" , "1");newtListboxAppendEntry(listbox, "PUTRA FOODCOURT" , "2");newtListboxAppendEntry(listbox, "LIBRARY" , "3");newtListboxAppendEntry(listbox, "FAKULTI BAHASA MODEN DAN KOMUNIKASI" , "4");newtListboxAppendEntry(listbox, "FAKULTI SAINS KOMPURTER DAN TEKNOLOGI MAKLUMAT" , "5");newtListboxAppendEntry(listbox, "FAKULTI SAINS" , "6");newtListboxAppendEntry(listbox, "FAKULTI BIOTEKNOLOGI DAN SAINS MOLEKUL" , "7");newtListboxAppendEntry(listbox, "FAKULTI ALAM SEKITAR" , "8");newtListboxAppendEntry(listbox, "FAKULTI KEJURUTERAAN" , "9");newtListboxAppendEntry(listbox, "FAKULTI PERUBATAN DAN SAINS PERUBATAN" , "10");newtListboxAppendEntry(listbox, "DEWAN KULIAH AKADEMI PUSAT" , "11");newtListboxAppendEntry(listbox, "KOLEJ 17" , "12");newtListboxAppendEntry(listbox, "KOLEJ 10" , "13");newtListboxAppendEntry(listbox, "FAKULTI REKABENTUK DAN SENI BINA" , "14");form1 = newtForm (NULL,NULL, 0 );newtFormAddComponents (form1,teks1,listbox,bOK,bCancel,label1,NULL);newtRunForm(form1);//selection = newtListboxGetCurrent (listbox);//newtFinished();//if(selection == NEWT_FLAG_BORDER)printf("You have make selection");newtFormDestroy(form1);newtFinished();}void time (char *input1C){newtComponent form, rbTime[16], label1, bOk;    int i;    const char teksTime[] = "Choose your time";    newtInit();    newtCls();    newtDrawRootText(-60, -2, teksTime);        newtOpenWindow(10,2,50,20,"EFFICIENT BUS SYSTEM");    label1 = newtLabel(10,1, teksTime);        rbTime[0] = newtRadiobutton(10,3,"8.00 am",1, NULL);    rbTime[1] = newtRadiobutton(10,4,"9.00 am",0,rbTime[0]);    rbTime[2] = newtRadiobutton(10,5,"10.00 am",0,rbTime[1]);    rbTime[3] = newtRadiobutton(10,6,"11.00 am",0,rbTime[2]);    rbTime[4] = newtRadiobutton(10,7,"12.00 pm",0,rbTime[3]);    rbTime[5] = newtRadiobutton(10,8,"1.00 pm",0,rbTime[4]);    rbTime[6] = newtRadiobutton(10,9,"2.00 pm",0,rbTime[5]);    rbTime[7] = newtRadiobutton(10,10,"3.00 pm",0,rbTime[6]);    rbTime[8] = newtRadiobutton(30,3,"4.00 pm",0,rbTime[7]);    rbTime[9] = newtRadiobutton(30,4,"5.00 pm",0,rbTime[8]);    rbTime[10] = newtRadiobutton(30,5,"6.00 pm",0,rbTime[9]);    rbTime[11] = newtRadiobutton(30,6,"7.00 pm",0,rbTime[10]);    rbTime[12] = newtRadiobutton(30,7,"8.00 pm",0,rbTime[11]);    rbTime[13] = newtRadiobutton(30,8,"9.00 pm",0,rbTime[12]);    rbTime[14] = newtRadiobutton(30,9,"10.00 pm",0,rbTime[13]);    rbTime[15] = newtRadiobutton(30,10,"11.00 pm",0,rbTime[14]);    bOk = newtButton(22,13,"OK");    form = newtForm(NULL, NULL, 0);        for( i=0; i<16; i++) {newtFormAddComponent(form,rbTime[i]);}    newtFormAddComponents(form, bOk,label1,NULL);    newtRunForm(form);    newtFormDestroy(form);    newtFinished();}
```

---

