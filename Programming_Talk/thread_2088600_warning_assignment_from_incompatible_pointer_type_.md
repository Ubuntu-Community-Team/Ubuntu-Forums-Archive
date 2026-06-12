---
title: "warning: assignment from incompatible pointer type (NesC)"
date: 2012-11-27
forum: Programming Talk
---

### Post by tzeronone on 2012-11-27
I am writing a programming code to operate accelerometer and SHT11 sensor. When I debug the code, there are warnings. Can teach me how to solve them?
 
```

#include "PacketMsg.h"
#include "I2C.h"
module FileM {
  uses {
    interface Boot;
    interface Leds;
    interface Timer<TMilli> as Timer1;
    interface Timer<TMilli> as Timer2;
    interface SplitControl as AMControl;
    interface GeneralIO as Pin_PW3;
    interface GeneralIO as Pin_PW4;
 
    interface Packet as Data_Packet ;
    interface AMSend as Data_AMSend;
    interface Receive as Data_Receive;
 
    interface CC2420Packet;
 
    interface BlockRead;
    interface BlockWrite;
 
    interface Read<uint16_t>;
    interface Resource;
    interface I2CPacket<TI2CBasicAddr> as I2C;
  }
}
implementation {
  uint32_t pkt_cnt;
  uint32_t ACK_ID;
  message_t pkt;
  message_t pkt_ACK;
  bool busy;
  uint16_t blk_count;
  uint32_t w_addr, r_addr;
  uint16_t tmp_data[1]; 
  uint8_t read_data[1];
  uint8_t send_done=0;
  PacketMsg* btrpkt;
  uint8_t state; 
  uint8_t temp[8] = {}; 
  uint8_t* ptr8; 
  /* Accelerometer */
  uint8_t turn;
  uint16_t batt_val;
  uint16_t accel1, accel2, accel3; 
  uint8_t* send_data_ptr;
  uint8_t* send_data_ptr2;
  uint8_t send_data;
  uint16_t send_data2;
  uint8_t* ptr;
  uint8_t temp_Accel[6] = {};
 
  enum { // Temp
    STATE1, STATE2, STATE3, STATE4
  };  
 
  /* Read Battery */
  task void ReadBatt() {
    call Read.read();
  }
 
  /* Battery Read */
  event void Read.readDone(error_t result, uint16_t data) {
    atomic {
      if(result==SUCCESS) 
       batt_val = data;
      else 
       batt_val = 0;
 
      if(turn!=1) // Set turn become 1 to start getting values
       turn = 1;
 
      call Timer1.startOneShot(20); 
    }
  }
 
  /* Accelerometer Resources Granted */
  event void Resource.granted() {
    call Leds.led0On();
    atomic {
      if(turn==0) {   // Set sensor to measure mode 00001000 to Address 2D
        send_data2 = 0x082D; 
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 2, send_data_ptr2);
      }
      else if(turn==1) { // Set sensor to write X0
        send_data = 0x32; 
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 1, send_data_ptr);
      }
    }
  }
 
  /* When write is done */
    async event void I2C.writeDone(error_t error, uint16_t addr, uint8_t length, uint8_t* data) {
    if(error==SUCCESS) call Leds.led2On();
    atomic {
      if(turn==0) {   // Involve Tap_x, Tap_y, Tap_z 00000111 to Address 2A
        send_data = 0x072A; 
        call I2C.read(I2C_START | I2C_STOP, 0xA7, 2, send_data_ptr); 
      }
      else {
        call I2C.read(I2C_START | I2C_STOP, 0xA7, 2, data);
      }
    }
  }
 
    async event void I2C.readDone(error_t error, uint16_t addr, uint8_t length, uint8_t* data) {
    if(error==SUCCESS) call Leds.led2Off();
    atomic {
      if(turn==0) {
        call Resource.release(); // Release the resource
        call Leds.led0Off();
        post ReadBatt();   // Read battery values
      }
      else if(turn==1) {    // store x0 read x1
        temp_Accel[0] = data[1];
        turn = 2;
        send_data = 0x33; 
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 1, send_data_ptr);
      }
      else if(turn==2) {    // store x1 read y0
        temp_Accel[1] = data[1];
        turn = 3;
        send_data = 0x34;
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 1, send_data_ptr);
      }
      else if(turn==3) {    // store y0 read y1
        temp_Accel[2] = data[1];
        turn = 4;
        send_data = 0x35; 
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 1, send_data_ptr);
      }
      else if(turn==4) {    // store y1 read z0
        temp_Accel[3] = data[1];
        turn = 5;
        send_data = 0x36; 
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 1, send_data_ptr);
      }
      else if(turn==5) {    // store z0 read z1
        temp_Accel[4] = data[1];
        turn = 6;
        send_data = 0x37; 
        call I2C.write(I2C_START | I2C_STOP, 0xA6, 1, send_data_ptr);
      }
      else if(turn==6) {    // store z1 
        temp_Accel[5] = data[1];
        call Resource.release(); // Release the resources
        call Leds.led0Off();
        atomic state = STATE4; 
        post ReadBatt();   // Call to read battery voltage
      }
    }
  }
 
  /* Temperature sensor gap waiting tome */
  void inline TOSH_uwait(int u_sec) { 
    while(u_sec>0) { //least than 1us
      asm volatile ("nop" ::);
      u_sec--;
    }
  }
 
  /* Checking sensor node is inside coverage area of BS or not */
  task void SendACK () { // 
    btrpkt = (PacketMsg*)(call Data_Packet.getPayload(&pkt, NULL)); // Call pointer
    btrpkt->nodeid = TOS_NODE_ID;
    if(!busy) {  //send data out
      if(call Data_AMSend.send(1, &pkt, sizeof(PacketMsg)) == SUCCESS) {
        busy = TRUE;
      }
    }
  }
 
   void Write(uint8_t x) {
    int i;
    for(i=7; i>=0; i--) {
      if(((x>>i)&1)==1) {
        call Pin_PW4.set();
        call Pin_PW3.set();
        TOSH_uwait(1);
        call Pin_PW3.clr();
      }
      else {
        call Pin_PW4.clr();
        call Pin_PW3.set();
        TOSH_uwait(1);
        call Pin_PW3.clr();
      }
    }
    call Pin_PW4.makeInput();
    call Pin_PW3.set();
    TOSH_uwait(1);
    call Pin_PW3.clr();
  }
 
  void Read2(uint8_t num_read_byte) {
    int i, j;
    for(j=0; j<num_read_byte; j++) {
      temp[j] = 0;
    }
    for(j=0; j<num_read_byte; j++) {
      for(i=7; i>=0; i--) {
        call Pin_PW3.set();
        TOSH_uwait(1);
        call Pin_PW3.clr();
        temp[j] = temp[j]|(call Pin_PW4.get()<<i);
      }
      call Pin_PW4.makeOutput();
      call Pin_PW4.clr();
      call Pin_PW3.set();
      TOSH_uwait(1);
      call Pin_PW3.clr();
      call Pin_PW4.makeInput();
    }
 
  }
 
  task void ReadData2() {
    Read2(3);
    TOSH_uwait(5);
    call Pin_PW4.makeOutput();
    call Pin_PW4.set();
    call Leds.led0Off();
    atomic state = STATE3;
    call Timer1.startOneShot(20); 
  }
 
  void SendCmd2() {
    Write(0x03);
    TOSH_uwait(5);
    atomic state = STATE2;
    call Timer1.startOneShot(20); //wait for 320ms
  }
 
   task void Signalling2() {
    call Pin_PW3.set();
    TOSH_uwait(1);
    call Pin_PW4.clr();
    TOSH_uwait(1);
    call Pin_PW3.clr();
    TOSH_uwait(1);
    TOSH_uwait(1);
    TOSH_uwait(1);
    call Pin_PW3.set();
    TOSH_uwait(1);
    call Pin_PW4.set();
    TOSH_uwait(1);
    call Pin_PW3.clr();
    TOSH_uwait(10);
    SendCmd2();
  }
  task void SendData() {
    btrpkt = (PacketMsg*)(call Data_Packet.getPayload(&pkt, NULL)); // Call pointer
    btrpkt->nodeid = TOS_NODE_ID;
    btrpkt->pktid = ++pkt_cnt;
    btrpkt->batt_val = batt_val;
 
    /* Temperature Data */
    ptr8 = (uint8_t*)&btrpkt->data_t;
    ptr8[0] = pkt.data[6]; 
    ptr8[1] = pkt.data[7]; 
 
    /* Accelerometer Data */
    ptr = (uint8_t*)&accel1;
    ptr[0] = pkt.data[8];
    ptr[1] = pkt.data[9];
 
    ptr = (uint8_t*)&accel2;
    ptr[0] = pkt.data[10];
    ptr[1] = pkt.data[11];
 
    ptr = (uint8_t*)&accel3;
    ptr[0] = pkt.data[12];
    ptr[1] = pkt.data[13];
 
    btrpkt->accel_val[0] = accel1;
    btrpkt->accel_val[1] = accel2;
    btrpkt->accel_val[2] = accel3;
 
 
    if(!busy) {  //send data out
      if(call Data_AMSend.send(1, &pkt, sizeof(PacketMsg)) == SUCCESS) {
        busy = TRUE;
      }
    }
  }
  /* (Storage_addr_t, void* buf, storage_len_t len) */
  task void WriteData() { // write data into memory
    call BlockWrite.write(w_addr, &temp[0], 10);
  }
 
  /* (storage_addr_t addr, void* buf, storage_len_t len) */
  task void ReadData() { // read data from memory
    atomic {
      call BlockRead.read(r_addr, &pkt.data[6], 10); 
      call Leds.led0Toggle();
    }
  }
  event void Boot.booted() {
    atomic {
      pkt_cnt = 0;
      busy = FALSE;
      blk_count = 0;
      w_addr = r_addr = 0;
      state = STATE1;
      send_data_ptr = &send_data;
      send_data_ptr2 = &send_data2;
      turn =0;
    }
 
    call Pin_PW3.makeOutput(); //SCK
    call Pin_PW3.clr();
    call Pin_PW4.makeOutput(); //DAT
    call Pin_PW4.set();
 
    call CC2420Packet.setPower(&pkt, 3); // -25dBm set the transmitter power
    call AMControl.start();
    call Timer1.startOneShot(20); 
  }
  event void AMControl.startDone(error_t err) {
   call Timer2.startPeriodic(1024); // Every 5 sec will send an ACK to BS
  }
  event void AMControl.stopDone(error_t err) {
  }
 
  event void Timer1.fired() {
    atomic {
   if(state == STATE1) {   // Temperature 1
  call Leds.led0On();
        post Signalling2();
   }
 
   else if (state == STATE2) { // Temperature 2
    post ReadData2(); 
   }
      else if(state==STATE3) {  // Accelerometer 1
        call Resource.request();
        //post WriteData(); 
      }
      else if(state==STATE4) {  // Write to flash memory
      atomic {
       temp[2] = temp_Accel[0];
       temp[3] = temp_Accel[1];
       temp[4] = temp_Accel[2];
       temp[5] = temp_Accel[3];
       temp[6] = temp_Accel[4]; 
       temp[7] = temp_Accel[5];
        post WriteData();  
      }  
      }   
    }
  }
 
  // For sending ACK purpose
  event void Timer2.fired() {
    post SendACK ();
  }
  event void Data_AMSend.sendDone(message_t* msg, error_t err) {
    if(&pkt==msg) {
      busy = FALSE;
      call Leds.led1Toggle();
    }
  }
 
  /* This function is to receive Msg reply from base station */
  event message_t* Data_Receive.receive(message_t* msg, void* payload, uint8_t len) {
    PacketRMsg* r = (PacketRMsg*)(call Data_Packet.getPayload(msg, NULL));
    if(r->nodeid==TOS_NODE_ID && r->pktid==pkt_cnt) {
     if(blk_count!=0) {
          post ReadData();
       }
      else {
      }
    }
    return msg;
  }
 
  event void BlockRead.readDone(storage_addr_t addr, void* buf, storage_len_t len, 
    error_t error) {
    atomic {
      blk_count--;
      r_addr+=8;
      r_addr%=262144;
      post SendData();
    }
    call Leds.led2Off();
  }
  event void BlockRead.computeCrcDone(storage_addr_t addr, storage_len_t len, 
    uint16_t crc, error_t error) {
  }
  event void BlockWrite.writeDone(storage_addr_t addr, void* buf, storage_len_t len, 
    error_t error) {
    atomic {
      blk_count++;
      w_addr+=8;
      w_addr%=262144;
    }
    atomic state = STATE1;
    call Timer1.startOneShot(25);
    call Leds.led2Toggle();
  }
  event void BlockWrite.eraseDone(error_t error) {
  }
  event void BlockWrite.syncDone(error_t error) {
  }
 
}

```
 
When i run "make micaz debug", it shows:
```

$ make micaz debug
mkdir -p build/micaz
    compiling FileC to a micaz binary
ncc -o build/micaz/main.exe -Os -O1 -g -fnesc-no-inline -finline-limit=100000 -
all -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=build/micaz/app.c -board=mic
sb -Ibuild/micaz -DDEFINED_TOS_AM_GROUP=0x22 -DCC2420_DEF_CHANNEL=26 -DTOSH_DAT
_LENGTH=64 -DIDENT_PROGRAM_NAME=\"FileC\" -DIDENT_USER_ID=\"Administrator\" -DI
ENT_HOSTNAME=\"pc-35cc1be777e8\" -DIDENT_USER_HASH=0x4f56ef88L -DIDENT_UNIX_TIM
=0x50b45585L -DIDENT_UID_HASH=0xd28691e4L -fnesc-dump=wiring -fnesc-dump='inter
aces(!abstract())' -fnesc-dump='referenced(interfacedefs, components)' -fnesc-d
mpfile=build/micaz/wiring-check.xml FileC.nc -lm
In file included from FileC.nc:7:
In component `FileM':
FileM.nc: In function `Boot.booted':
FileM.nc:311: warning: assignment from incompatible pointer type
FileM.nc: In function `FileM$Boot$booted':
FileM.nc:311: warning: assignment from incompatible pointer type
FileM.nc: In function `FileM$I2C$writeDone':
FileM.nc:100: warning: large integer implicitly truncated to unsigned type
    compiled FileC to build/micaz/main.exe
           32154 bytes in ROM
             491 bytes in RAM
avr-objcopy --output-target=srec build/micaz/main.exe build/micaz/main.srec
avr-objcopy --output-target=ihex build/micaz/main.exe build/micaz/main.ihex
    writing TOS image

```

---

### Post by spjackson on 2012-11-27
I know nothing about NesC. However, with a C hat on, I think:

Your pointer warning is about this:
```

  uint8_t* send_data_ptr2;
  uint16_t send_data2;
  
  send_data_ptr2 = &send_data2;

```
Should this data item be 8 bits or 16?

Your warning about integer truncation is about this:
```
      
  uint8_t send_data;
  send_data = 0x072A;

``` 
That value is too large for an 8-bit unsigned integer.

---

### Post by tzeronone on 2012-11-28
Hi spjackson, if the data is 16 bit, may I know which part to change? I might be ask too much. But, I really need to avoid the warning...

---

### Post by spjackson on 2012-11-28
If both data items send_data and send_data2 are 16-bit, then you need to change 8 to 16 in these 2 lines
```

uint8_t* send_data_ptr2;
uint8_t send_data;

```

---

### Post by tzeronone on 2012-12-03
Hi spjackson, I have change it according to your opinion:
```

  /* Accelerometer */
  uint8_t turn;
  uint16_t batt_val;
  uint16_t accel1, accel2, accel3; 
  uint8_t* send_data_ptr;
  uint16_t* send_data_ptr2;
  uint16_t send_data;
  uint16_t send_data2;
  uint8_t* ptr;
  uint8_t temp_Accel[6] = {};

```
 
But it still has another warning:
```

$ make micaz
mkdir -p build/micaz
    compiling FileC to a micaz binary
ncc -o build/micaz/main.exe -Os -finline-limit=100000 -Wall -Wshadow -Wnesc-all
-target=micaz -fnesc-cfile=build/micaz/app.c -board=micasb -Ibuild/micaz -DDEFI
ED_TOS_AM_GROUP=0x22 -DCC2420_DEF_CHANNEL=26 -DTOSH_DATA_LENGTH=64 -DIDENT_PROG
AM_NAME=\"FileC\" -DIDENT_USER_ID=\"Administrator\" -DIDENT_HOSTNAME=\"pc-35cc1
e777e8\" -DIDENT_USER_HASH=0x4f56ef88L -DIDENT_UNIX_TIME=0x50bd7105L -DIDENT_UI
_HASH=0x5a83c544L -fnesc-dump=wiring -fnesc-dump='interfaces(!abstract())' -fne
c-dump='referenced(interfacedefs, components)' -fnesc-dumpfile=build/micaz/wiri
g-check.xml FileC.nc -lm
In file included from FileC.nc:7:
In component `FileM':
FileM.nc: In function `Resource.granted':
FileM.nc:86: warning: passing argument 4 of `I2C.write' from incompatible point
r type
FileM.nc: In function `Boot.booted':
FileM.nc:310: warning: assignment from incompatible pointer type
FileM.nc: In function `FileM$Resource$granted':
FileM.nc:86: warning: passing arg 4 of `FileM$I2C$write' from incompatible poin
er type
FileM.nc: In function `FileM$Boot$booted':
FileM.nc:310: warning: assignment from incompatible pointer type
    compiled FileC to build/micaz/main.exe
           19774 bytes in ROM
             492 bytes in RAM
avr-objcopy --output-target=srec build/micaz/main.exe build/micaz/main.srec
avr-objcopy --output-target=ihex build/micaz/main.exe build/micaz/main.ihex
    writing TOS image

```

---

### Post by tzeronone on 2012-12-12
Solved):p

---

### Post by dwhitney67 on 2012-12-12
> **tzeronone said:**
> Solved):p

Then mark your thread as SOLVED.

---

