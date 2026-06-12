---
title: "EXPECT-Problem detecting telnet prompt"
date: 2008-08-11
forum: Programming Talk
---

### Post by ranthal on 2008-08-11
So I have set up a bash script that sets options and calls an expect script that spawns a telnet session which can have multiple prompts. The expect statement is having trouble detecting the prompt though I can clearly see that it appears. Before I get into too much detail here is the code in brief:

set prompt "(BDI>|bft_8250>|bft_fpga>|bft_kernel>) $"; #multiple possible prompt commands

# Call to telnet process
BDITelnet $GlobalData(configFile) $prompt $GlobalData(bdiIPAddress) $GlobalData(hostIPAddress) $GlobalData(progEnable) $GlobalData(flashFile)

#Telnet function
proc BDITelnet { configFile configPrompt bdiIPAddress hostIPAddress bdiProg flashFile } {
...
expect \
$configPrompt \
{ send "res halt\r" } \
timeout \
{ set status 1; \
set GlobalData(errorMessage) "Waiting for prompt failed" }
...
}

It keeps timing out and the prompt as it appears in the telnet seesion is "bft_8250>". Any ideas? Is it a reg ex/or problem? Post questions if you have them, I kept tried to keep it short so might be more I need to clear up.

---

### Post by ranthal on 2008-08-11
So I went with:
set prompt ">$"
and the script works fine now.  But I am still curios if anyone knows why it wouldn't process the or list correctly?  I also got it to work with:
set prompt "bft_8250>$"
but once I start loading the kernel and some FPGA stuff into the board it will have different prompts (such as "bft_kernel>$") so the shorter version is what I am going with.

---

