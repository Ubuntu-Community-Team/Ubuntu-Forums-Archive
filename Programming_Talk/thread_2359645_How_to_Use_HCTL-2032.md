---
title: "How to Use HCTL-2032"
date: 2017-04-26
forum: Programming Talk
---

### Post by lilima on 2017-04-26
Good morning,
I would like to ask you some advice about HCTL-2032. My conditions is given below.
I myself drawn a board to measure the speed of machine according to the datasheet of [HCTL-2032-SC]("http://www.kynix.com/uploadfiles/pdf0125/HCTL-2032-SC.pdf"). But after a long time to debug it,I didn’t got a result cause it can’t get the digital value of encoder’s pulse in test. The output of encoder is normal while the HCTL-2032-SC is new. The clock output PWM wave--3KHz by cpu. Here I don’t think the circuit has problems because I drawn it by referring to the datasheet.The program which is as following has changed many time.
```
void init()      //Here using two orthogonal decoding chip to measure four orthogonal signal
{
//**********************HCTL2032 pin initialization ************

   gpio_init (PORTA,26,GPO,LOW);       //1RESETX=0   value reset  resetting after getting data every time
   gpio_init (PORTA,27,GPO,LOW);       //1RESETY=0
   gpio_init (PORTA,26,GPO,HIGH);      //reset and calculating again
   gpio_init (PORTA,27,GPO,HIGH);

   gpio_init (PORTA,6, GPO,HIGH);      //1EN1=1      choose calculating mode 1X
   gpio_init (PORTA,7, GPO,HIGH);      //1EN2=1
   gpio_init (PORTA,14,GPO,HIGH);      //1SEL1=1&#65292;
   gpio_init (PORTA,15,GPO, LOW);      //1SEL2=0&#65292;read value LSB first&#65288;Here just need one bit&#65292;so just readLSB&#65289;
   gpio_init (PORTA,4, GPO,HIGH);      //1OE/=1    Three states output the buffet control end&#65292;effect low level

   gpio_init (PORTB,6, GPI,LOW);       //1U/DX    read A&#12289;B to judge signal&#65292;a before b is1&#65292;or not is 0
   gpio_init (PORTB,7, GPI,LOW);       //1U/DY

   gpio_init (PORTB,10,GPI,LOW);       //read U1 digital port,set (1D0-1D7) to input(0)
   gpio_init (PORTB,18,GPI,LOW);
   gpio_init (PORTB,19,GPI,LOW);
   gpio_init (PORTB,20,GPI,LOW);
   gpio_init (PORTC,5, GPI,LOW);
   gpio_init (PORTC,7, GPI,LOW);
   gpio_init (PORTC,6, GPI,LOW);
   gpio_init (PORTC,8, GPI,LOW);


   gpio_init (PORTA,28,GPO, LOW);       //2RESETX=0   value reset  resetting after getting data every time
   gpio_init (PORTA,29,GPO, LOW);       //2RESETY=0
   gpio_init (PORTA,28,GPO,HIGH);       //reset and calculating again
   gpio_init (PORTA,29,GPO,HIGH);

   gpio_init (PORTA,12,GPO,HIGH);      //2EN1=1     choose calculating mode 1X
   gpio_init (PORTA,13,GPO,HIGH);      //2EN2=1
   gpio_init (PORTA,16,GPO,HIGH);       //2SEL1=1&#65292;
   gpio_init (PORTA,19,GPO, LOW);       //2SEL2=0&#65292;read value LSB  first&#65288;Here just need one bit&#65292;so just read LSB&#65289;   
  gpio_init (PORTA,5, GPO,HIGH);      //2OE/=1

   gpio_init (PORTB,8, GPI,LOW);      //2U/DX
   gpio_init (PORTB,9, GPI,LOW);      //2U/DY

   gpio_init (PORTC,9, GPI,LOW);      //read U2 digital port,set (2D0-2D7) to input(0)
   gpio_init (PORTC,10,GPI,LOW);
   gpio_init (PORTC,11,GPI,LOW);
   gpio_init (PORTC,12,GPI,LOW);
   gpio_init (PORTC,13,GPI,LOW);
   gpio_init (PORTC,14,GPI,LOW);
   gpio_init (PORTC,15,GPI,LOW);
   gpio_init (PORTD,0, GPI,LOW);

   FTM_PWM_init(FTM2, CH1,3000,1500);//HCTL2032 clock initialization is 3KHz
}

/************************************** orthogonal decoding test speed /MADE BY CSH*******************
*
*  function name&#65306;getDataHCTL2032
*  function&#65306;chip HCTL-2032 to count&#65292;orthogonal decoding test speed
* reference&#65306;model:coreNum&#65292;xy is channel number
*  returned value&#65306;none
*  modified time&#65306;2017-04-14    waiting for testing
*  remark&#65306;
**************************************************************************/
void  getDataHCTL2032(int8 coreNum,int8 xy)
{
  int pic[8];

//////////////////////////////read U1orthogonal decoding data///////////////////////////////

  if(coreNum==0)
  {
    gpio_set (PORTA,4,  0);      //1OEenable

    if(xy==0)
    {
       gpio_set (PORTA,24, 0);     //1XY=0chose X axle
    // gpio_set (PORTA,14,HIGH);     //1SEL1=1&#65292;
    // gpio_set (PORTA,15, LOW);     //1SEL2=0&#65292;read value LSB first
       pic[0]=gpio_get(PORTB,10);    // get the eight low value
       pic[1]=gpio_get(PORTB,18);
       pic[2]=gpio_get(PORTB,19);
       pic[3]=gpio_get(PORTB,20);
       pic[4]=gpio_get(PORTC, 5);
       pic[5]=gpio_get(PORTC, 7);
       pic[6]=gpio_get(PORTC, 6);
       pic[7]=gpio_get(PORTC, 8);

       direction1=gpio_get(PORTB, 6);       //get A1machine Positive and negative turn signal&#65292;
                                            //direction1=1 is positive turn signal (CHA before CHB/count )&#65292;&#20026;0 is negative turn signal (CHB before CHA/count)

       gpio_set(PORTA,26,0);                //finish reading data&#65292;restoration 1X
       gpio_set(PORTA,26,1);                //reset and calculating again

       for(int i=0;i<8;i++)                //digital value changes to be Decimal value    
  {
         if(pic[i]==1)
         currentSpeed1+=pow(2,i);           //save ring1 speed       }
     }
     else if(xy==1)
     {
       gpio_set (PORTA,24,1);        //1XY=1chose Y axle 
    // gpio_set (PORTA,14,HIGH);     //1SEL1=1&#65292;
    // gpio_set (PORTA,15, LOW);     //1SEL2=0&#65292;read value LSB first
//time_delay_ms(5);

       pic[0]=gpio_get(PORTB,10);    //get the eight low value
       pic[1]=gpio_get(PORTB,18);
       pic[2]=gpio_get(PORTB,19);
       pic[3]=gpio_get(PORTB,20);
       pic[4]=gpio_get(PORTC, 5);
       pic[5]=gpio_get(PORTC, 7);
       pic[6]=gpio_get(PORTC, 6);
       pic[7]=gpio_get(PORTC, 8);

       direction2=gpio_get(PORTB, 7);    //get A1machine Positive and negative turn signal&#65292;

                                         //direction2=1is positive turn signal (CHA before CHB/count )&#65292;&#20026;0 is negative turn signal (CHB before CHA/count)

       gpio_set(PORTA,27,0);        //finish reading data&#65292;restoration 1Y
       gpio_set(PORTA,27,1);        //reset and calculating again
       for(int i=0;i<8;i++)         //digital value changes to be Decimal value 
       {
         if(pic[i]==1)
         currentSpeed2+=pow(2,i);   //save ring1 speed       }
     }
  /*
    gpio_set (PORTA,14,0);   /read 2ND
    gpio_set (PORTA,15,0);
  //time_delay_ms(1);

    pic[8]=gpio_get(PORTB, 10);
    pic[9]=gpio_get(PORTB, 18);
    pic[10]=gpio_get(PORTB, 19);
    pic[11]=gpio_get(PORTB, 20);
    pic[12]=gpio_get(PORTC, 5);
    pic[13]=gpio_get(PORTC, 7);
    pic[14]=gpio_get(PORTC, 6);
    pic[15]=gpio_get(PORTC, 8);
    for(int i=8;i<16;i++)
    {
       if(pic[i]==1)
       *speed+=pow(2,i);
     }
   */
    gpio_set (PORTA,4, 1);        //1OE banned
  }
```

The U2 program is similar to the U1.
What’s wrong? Could you help me out?
Thanks.
Wishes~

---

