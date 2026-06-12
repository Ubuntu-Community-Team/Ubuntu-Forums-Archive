---
title: "gpsd cycle time"
date: 2015-07-01
forum: New to Ubuntu
---

### Post by Vinayaka_Negalur on 2015-07-01
Hello,

I am new to these forums. 

I aam trytin gto capture GPS data from ublox M8 sensor. But the timing by default is set to 1s. 
I need to have the GPS data captured it once every 500ms. I tried using gpsctl utility. When I set the value to 0.5, I see that there is no data for long time from GPS sensor.
The output from the gpsctl is posted below.

```
root@root:~# gpsctl -D 5 -c 0.5
libgps: gps_sock_open(localhost, 2947)
libgps: netlib_connectsock() returns socket on fd 3
libgps: gps_read() begins
libgps: gps_unpack({"class":"VERSION","release":"3.14","rev":"3.14","proto_major                                 ):3,"proto_minor":10}
libgps: gps_unpack() segment parse '{"class":"VERSION","release":"3.14","rev":"3                                 '14","proto_major":3,"proto_minor":10}
flags: (0x10000000) {VERSION}
VERSION: release=3.14 rev=3.14 proto=3.10
libgps: final flags: (0x10000000) (null)
libgps: gps_read() -> 84 ({PACKET|VERSION})
libgps: gps_read() begins
libgps: gps_unpack({"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01 (75350)","activated":"2015-07-01T13:45:00.611Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits")1,"cycle":1.00,"mincycle":0.25}]}
libgps: gps_unpack() segment parse '{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01 (75350)","activated":"2015-07-01T13:45:00.611Z","flags":1,"native":0,"bps":9600,"parit'":"N","stopbits":1,"cycle":1.00,"mincycle":0.25}]}
flags: (0x100000) {DEVICELIST}
DEVICELIST:1 devices:
1: path='/dev/ttyACM0' driver='u-blox'
libgps: final flags: (0x100000) (null)
libgps: gps_read() -> 243 ({DEVICELIST|PACKET})
libgps: gps_read() begins
libgps: gps_unpack({"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01 (75350)","activated":"2015-07-01T13:45:04.615Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits":1,"cycle":0.50,"mincycle":0.2)}
libgps: gps_unpack() segment parse '{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01 (75350)","activated":"2015-07-01T13:45:04.615Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits":1,"cycle":0.'0,"mincycle":0.25}
flags: (0x180000) {DEVICE|DEVICELIST}
DEVICE: Device is '/dev/ttyACM0', driver is 'u-blox'
DEVICELIST:1 devices:
1: path='/dev/ttyACM0' driver='u-blox'
libgps: final flags: (0x180000) (null)
libgps: gps_read() -> 211 ({DEVICE|DEVICELIST|PACKET})
libgps: gps_close()
root@nvidia:~/PosService-Integrated-v0.4-2506/TestClient# gpsctl -D 5
libgps: gps_sock_open(localhost, 2947)
libgps: netlib_connectsock() returns socket on fd 3
libgps: gps_read() begins
)ibgps: gps_unpack({"class":"VERSION","release":"3.14","rev":"3.14","proto_major":3,"proto_minor":10}
libgps: gps_unpack() segment parse '{"class":"VERSION","release":"3.14","rev":"3.14","proto_major":3,"proto_minor':10}
flags: (0x10000000) {VERSION}
VERSION: release=3.14 rev=3.14 proto=3.10
libgps: final flags: (0x10000000) (null)
libgps: gps_read() -> 84 ({PACKET|VERSION})
libgps: gps_read() begins
libgps: gps_unpack({"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01 (75350)","activated":"2015-07-01T13:46:09.832Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits")1,"cycle":0.50,"mincycle":0.25}]}
libgps: gps_unpack() segment parse '{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01 (75350)","activated":"2015-07-01T13:46:09.832Z","flags":1,"native":0,"bps":9600,"parit'":"N","stopbits":1,"cycle":0.50,"mincycle":0.25}]}
flags: (0x100000) {DEVICELIST}
DEVICELIST:1 devices:
1: path='/dev/ttyACM0' driver='u-blox'
libgps: final flags: (0x100000) (null)
libgps: gps_read() -> 243 ({DEVICELIST|PACKET})
/dev/ttyACM0 identified as a u-blox 2.01 (75350) at 9600 baud.
libgps: gps_close()

```

Please help me in getting/configuring the GPS sensor to receive the data once every 500ms.
As of now, I am using the watch to measure the rate. Do you already know any standard method which can capture time stamp also?

BR,
Vinayaka

---

### Post by Bucky Ball on 2015-07-01
Please give details of the Ubuntu flavour and release you are using.

---

### Post by tgalati4 on 2015-07-01
Many GPS devices will only output data to 1-second intervals.  This is for safety purposes.  To get finer details, you need to either interpolate yourself in code, or get a different GPS receiver.  The TTFF (I presume Time To First Fix) is specified as 1 second, so you will get no data when there is missing satellites, indoors, under heavy trees, or clouds.  It typically takes several seconds for a GPS receiver to get a "lock" on initial position (TTFF) and then position data will be pumped out at whatever rate you tell it to.

The documentation on the M8 shows that it can take 180 seconds for acquisition with weak signals.  What is the fastest that the chip says it will output its data stream?

It's also possible that at 9600 baud, you can't get reliable communication for the faster data rate.  Try 38400 or higher.

---

### Post by Vinayaka_Negalur on 2015-07-02
Thanks tgalati4 for the response.
Currently the data is read at 9600 baud. And since I am in an open area (not congested area), I assume that there is no issue of missing satellites.

Now the question is how to check if the sensor supports 500ms rate?. I did not find any detail to query the supported rate. I could not find any detail about how to change the rate using the commands.
Any hint of how to check and set the same?

---

### Post by Vinayaka_Negalur on 2015-07-02
> **Bucky Ball said:**
> Please give details of the Ubuntu flavour and release you are using.

root@root:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty

---

### Post by dino99 on 2015-07-02
gpsd itself has 1 second limit
 >   -c
           Change the GPS´s cycle time. Units are seconds. Note, most GPses
           have a fixeed cycle time of 1 second.

- f  & - s options could help too [http://manpages.ubuntu.com/manpages/vivid/man1/gpsctl.1.html](http://manpages.ubuntu.com/manpages/vivid/man1/gpsctl.1.html)

---

### Post by Vinayaka_Negalur on 2015-07-02
Yes dino. This was already tried out. If you see my initial query, it shows that gpsctl was run with -c 0.5 as parameters. gpsctl debug logs also show that it is set.

"cycle":0.50,"mincycle":0.25

And the issue after that is there is no gps data received periodically and values are received once in ~40-50s. 
the data is not received periodically until the target is restarted.

---

### Post by Vinayaka_Negalur on 2015-07-02
btw, I am using gpsd 3.14 version.
I see in gpsd code (driver_ubx.c) that the position data is printed. But these prints are neither seen in any logs, nor in the console from where gpsd is launched. 
How do I see the below such logs? I am launching gpsd with -D 5 as option.

```

    gpsd_log(&session->context->errout, LOG_DATA,
         "NAVSOL: time=%.2f lat=%.2f lon=%.2f alt=%.2f track=%.2f speed=%.2f climb=%.2f mode=%d status=%d used=%d\n",
         session->newdata.time,
         session->newdata.latitude,
         session->newdata.longitude,
         session->newdata.altitude,
         session->newdata.track,
         session->newdata.speed,
         session->newdata.climb,
         session->newdata.mode,
         session->gpsdata.status,
         session->gpsdata.satellites_used);

```

---

### Post by tgalati4 on 2015-07-02
Send an email to the manufacturer with your rate questions.  The GPS devices that I have used in the past were all limited to 1-second data output.  Higher rates are generally restricted to military uses.

---

### Post by Vinayaka_Negalur on 2015-07-07
Hi again,

I was able to set the measurement rate using u-center tool that is provided by uBlox.

---

