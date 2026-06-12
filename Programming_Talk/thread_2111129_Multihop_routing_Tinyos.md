---
title: "Multihop routing Tinyos"
date: 2013-02-01
forum: Programming Talk
---

### Post by tzeronone on 2013-02-01
I have a a sensor node that able to send temperature data. 

```
#include "PacketMsg.h"

module ADC_rawM {
  uses interface Boot;
  uses interface Leds;
  uses interface GeneralIO as Pin1;
  uses interface Timer<TMilli> as Timer1;
  uses interface Timer<TMilli> as Timer2;
  uses interface SplitControl as AMControl;
  uses interface Packet;
  uses interface AMPacket;
  uses interface AMSend;
  uses interface Receive;
  
  uses interface Read<uint16_t>;
  uses interface Atm128AdcSingle as Adc;
}

implementation {
  uint32_t cnt;
  uint8_t turn;
  uint16_t adc1, adc2, adc3, adc4, adc5, adc6;
  uint16_t batt_val;
  message_t pkt;
  bool busy;

  task void SendData() {
    PacketMsg* btrpkt = (PacketMsg*)(call Packet.getPayload(&pkt, NULL));
    atomic {
      btrpkt->nodeid = TOS_NODE_ID;
      btrpkt->pktid = ++cnt;
      btrpkt->adc1 = adc1;
      btrpkt->adc2 = adc2;
      btrpkt->adc3 = adc3;
      btrpkt->adc4 = adc4;
      btrpkt->adc5 = adc5;
      btrpkt->adc6 = adc6;
      btrpkt->batt_val = batt_val;
    }
    if(!busy) {
      if(call AMSend.send(AM_BROADCAST_ADDR, &pkt, sizeof(PacketMsg)) == SUCCESS) {
        busy = TRUE;
      }
    }
    else call Leds.led2Toggle();
  }
  
  task void Get_ADC() {
    atomic turn++;
    call Timer2.startPeriodic(10);
  }

  event void Boot.booted() {
    atomic {
      cnt = 0;
      turn = 0;
      busy = FALSE;
    }
    call Pin1.makeOutput();
    call Pin1.set();
    call AMControl.start();
  }
  
  event void AMControl.startDone(error_t err) {
    if(err==SUCCESS) {
      call Timer1.startPeriodic(256);
    }
    else {
      call Leds.led0On();
    }
  }

  event void AMControl.stopDone(error_t err) {
  }

  event void Timer1.fired() {
    call Read.read();
  }
  
  event void Timer2.fired() {
    atomic {
      if(turn==1) call Adc.getData(ATM128_ADC_SNGL_ADC1, ATM128_ADC_VREF_OFF, FALSE, ATM128_ADC_PRESCALE);
      if(turn==2) call Adc.getData(ATM128_ADC_SNGL_ADC2, ATM128_ADC_VREF_OFF, FALSE, ATM128_ADC_PRESCALE);
      if(turn==3) call Adc.getData(ATM128_ADC_SNGL_ADC3, ATM128_ADC_VREF_OFF, FALSE, ATM128_ADC_PRESCALE);
      if(turn==4) call Adc.getData(ATM128_ADC_SNGL_ADC4, ATM128_ADC_VREF_OFF, FALSE, ATM128_ADC_PRESCALE);
      if(turn==5) call Adc.getData(ATM128_ADC_SNGL_ADC5, ATM128_ADC_VREF_OFF, FALSE, ATM128_ADC_PRESCALE);
      if(turn==6) call Adc.getData(ATM128_ADC_SNGL_ADC6, ATM128_ADC_VREF_OFF, FALSE, ATM128_ADC_PRESCALE);
    }
  }

  event void AMSend.sendDone(message_t* msg, error_t err) {
    if(&pkt==msg) {
      busy = FALSE;
      call Leds.led1Toggle();
    }
  }

  event message_t* Receive.receive(message_t* msg, void* payload, uint8_t len) {
    return msg;
  }

  event void Read.readDone(error_t result, uint16_t data) {
    atomic {
      if(result==SUCCESS) batt_val = data;
      else batt_val = 0;
    }
    post Get_ADC();
  }

  async event void Adc.dataReady(uint16_t data, bool precise) {
    atomic {
      if(turn==1) {
        adc1 = data;
        post Get_ADC();
      }
      if(turn==2) {
        adc2 = data;
        post Get_ADC();
      }
      if(turn==3) {
        adc3 = data;
        post Get_ADC();
      }
      if(turn==4) {
        adc4 = data;
        post Get_ADC();
      }
      if(turn==5) {
        adc5 = data;
        post Get_ADC();
      }
      if(turn==6) {
        adc6 = data;
        turn = 0;
        post SendData();
      }
    }
  }

}
```

May I know what code should I add in so that the sensor node able to become the router for another node and at the same time also produce data and send it to the base station?

---

