---
title: "Getting Logitech Setpoint to work in Guest"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by ldewittleedy on 2012-06-20
I have been trying this for a while now with no luck because setpoint doesnt support Linux atm nor do i feel they ever will :(
 
I have Linux Ubuntu 12.04 with Vmware Workstation 8.x.x installed on it with Windows 7 x64 as a guest os.
 
Before i made my windows 7 into a virtual(when i was useing it as the host) setpoint worked. but for some reason now that i have it virtualized it doesnt seem to see my Performance MX mouse in Setpoint. Setpoint works and is on yet it doesnt read my mouse so all my buttons dont work except right+left click and scroll.
 
When i go up to VM-->Removable Devices-->Logitech USB Receiver-->Connect(disconnect from host) it tells me:
 
"This VM is trying to claim 'Logitech USB Receiver'. If you continue, the device will no longer be usable in the host."
 
I can either press continue and it will see my mouse but it doesnt let me full screen because it "disconnects" from the host so i cant use it on the host till i "alt M" to get the removable devices and select "Disconnect (connect to the host)" then i can use it for host and guest but then setpoint doesnt see it again.
 
I guess my question is: Is there a way to share the mouse with Host and Guest so that i get full function inside my guest and still be able to use my mouse on the host.
 
Thanks,
Lance DeWitt,
IT at Leedy Mfg Co LLC.

---

### Post by ldewittleedy on 2012-06-22
Bump for the weekend, maybe someone with some spare time on their weekend will know about this issue.
 
I've been trying various things i find off google none have helped except adding  usb.generic.allowHID = "TRUE" and mouse.vusb.enable = "TRUE" in my .VMX file. but this wont allow for me to use the mouse with the host(ubuntu) unless i disable the mouse in the guest, but then i cant use it in the guest.
 
 
Appreciate any input on this.
 
Thanks,
Lance DeWitt.
IT at Leedy Mfg Co LLC.

---

### Post by ldewittleedy on 2012-07-11
Gave up on this...Thread can be deleted.

---

