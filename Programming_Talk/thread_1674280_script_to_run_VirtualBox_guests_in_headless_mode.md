---
title: "script to run VirtualBox guests in headless mode"
date: 2011-01-23
forum: Programming Talk
---

### Post by phoenix122 on 2011-01-23
Hi Everyone!
 
I use VirtualBox constantly, and other than creating a new machine using the gui, i mostly run my guests in headless mode. I wanted a script that would create a list of currently registered virtual machines, and allow me to run them. 

After reading the bash cookbook, searching the forums and Googling until the wee hours of the morning, its finally done :D , so i figured I'd share it as my first post.

This is the first script i've attempted, so its not the prettiest, and i'm sure there's an easier way to do some of it. comments and suggestions on how to improve it would be appreciated. 

Thanks! 

```

#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}

function error_exit 
{
	# Display error message and exit
	echo ""
	echo "${PROGNAME}: ${1:-"Unknown Error"}" 1>&2
	clean_up 1
}

 function press_enter 
{
	echo ""
	echo -n "Press Enter to continue"
	read
	clear
}

#############################################################
# Main Functions for starting a headless VM

function default_options
{
	echo ""
	echo -n "Enable VirtualBox Remote Display Protocol(y/n)?: "	
	read response
	echo ""
		case $response in
			[yY] ) vrde= ; echo "VDRP Enabled" ;;
			[nN] ) vrde="--vrde off" ; echo "VDRP Disabled" ;;
			* ) echo "Please enter yes or no (y/n)" ;;
		esac
}

function vm_starter
{   
	#Edit the output to remove the UUID and redirect the output
	VBoxManage --nologo list vms | sed -e 's/{.*}//g' > $TEMP_FILE
	# Re-run command, cut the Machine Name, braces, and whitespace, 
	# This goes into a different tempfile and user choice is taken from it
	VBoxManage --nologo list vms \
	| sed -e 's/".*"//g;s/[}]//;s/[{]//;s/^[ \t]*//;s/[ \t]*$//' > $TEMP_FILE2

	while [[ 1 ]] ; do
		echo "Currently Available Virtual Machines"
		echo ""
		cat -n "$TEMP_FILE"
		nr=$( cat "${TEMP_FILE}" | wc -l )
		read -p "Please make a selection, select q to quit: " choice
		case $choice in
			# Check for digits
			+([0-9])) do_action ;;
			q|Q) clear ; break ;;
			*) echo "Invalid choice" ; press_enter ;;
    	esac
done
}

function do_action
{
	runline=$(sed -n "$choice""p" "$TEMP_FILE2")
	line=$(sed -n "$choice""p" "$TEMP_FILE") 
	clear ; echo "" 
	echo "Starting $line Machine"	
	VBoxHeadless --startvm "$runline" $vrde
}


function list_vm 
{   #uncomment to hide Virtual Machine UUID 
	echo "" "Virtual Machine Info:"
    VBoxManage --nologo list vms | nl #| sed -e 's/{.*}//g'
	
}

#############################################################

if [ -d ~/tmp ]; then
	TEMP_DIR=~/tmp
else
	TEMP_DIR=/tmp
fi

selection= 
vrde="--vrde off" 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ "$selection" = "0" ]; do
    echo "Virtual Machine Menu"
	echo ""
    echo "1 - Start a Virtual Machine with default options"
    echo "2 - Change default options"
	echo "3 - View current Virtual Machines"
	echo ""
    echo "0 - Exit"
	echo ""
    echo -n "Enter selection: "
    read selection
    echo ""
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo "Please enter 1, 2, or 0"
    esac
done

```

---

### Post by phoenix122 on 2011-02-10
:confused: anything? I love these forums because the advice and help is useful, but i'm not feeling the love

---

### Post by sdowney717 on 2011-02-11
works and yet does not work
screenshot show that headless process starts.
in the VM manager gui, it shows the vm running
BUT, I never get the window box of the machine

terminal output. I saved the batch file as vbox.sh and made it executable

```
Virtual Machine Menu

1 - Start a Virtual Machine with default options
2 - Change default options
3 - View current Virtual Machines

0 - Exit

Enter selection: 1
Currently Available Virtual Machines

     1	"mythbuntu" 
     2	"mythdownload" 
     3	"minixp" 
     4	"xppro32" 
     5	"haiku" 
     6	"xppro322" 
Please make a selection, select q to quit: 3




Starting "minixp"  Machine
Oracle VM VirtualBox Headless Interface 4.0.2
(C) 2008-2011 Oracle Corporation
All rights reserved.




```

---

### Post by sdowney717 on 2011-02-11
here is the log of the process and shows headless runs
```
00:00:00.022 VirtualBox 4.0.2 r69518 linux.x86 (Jan 18 2011 19:58:28) release log
00:00:00.022 Log opened 2011-02-11T13:01:08.320437000Z
00:00:00.022 OS Product: Linux
00:00:00.022 OS Release: 2.6.35-25-generic
00:00:00.022 OS Version: #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011
00:00:00.022 DMI Product Name: P5QC
00:00:00.022 DMI Product Version: System Version
00:00:00.023 Host RAM: 3275MB RAM, available: 2025MB
00:00:00.023 Executable: /usr/lib/virtualbox/VBoxHeadless
00:00:00.023 Process ID: 3978
00:00:00.023 Package type: LINUX_32BITS_UBUNTU_10_10
00:00:00.052 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf8989020 - ModuleInit at 00000000f899ed40 and ModuleTerm at 00000000f899ed10
00:00:00.052 SUP: VMMR0EntryEx located at 00000000f899ebf0, VMMR0EntryFast at 00000000f899dcc0 and VMMR0EntryInt at 00000000f899db10
00:00:00.067 File system of '/home/scott/.VirtualBox/Machines/minixp/Snapshots' (snapshots) is unknown
00:00:00.067 File system of '/home/scott/.VirtualBox/HardDisks/minixp.vdi' is ext4
00:00:00.084 VBoxSharedClipboard mode: Bidirectional
00:00:00.086 ************************* CFGM dump *************************
00:00:00.086 [/] (level 0)
00:00:00.086   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:00.086   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:00.086   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:00.086   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:00.086   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:00.086   Name            <string>  = "minixp" (cb=7)
00:00:00.086   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:00.086   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:00.086   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:00.086   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:00.086   RamSize         <integer> = 0x000000001b400000 (457179136)
00:00:00.086   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:00.086   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:00.086   SyntheticCpu    <integer> = 0x0000000000000000 (0)
00:00:00.086   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:00.086   UUID            <bytes>   = "24 f1 41 f0 5e 47 40 4e 93 c5 23 99 90 6c b4 8b" (cb=16)
00:00:00.086 
00:00:00.086 [/CPUM/] (level 1)
00:00:00.086 
00:00:00.086 [/Devices/] (level 1)
00:00:00.086 
00:00:00.086 [/Devices/8237A/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/8237A/0/] (level 3)
00:00:00.086   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/AudioSniffer/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/AudioSniffer/0/] (level 3)
00:00:00.086 
00:00:00.086 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:00.086 
00:00:00.086 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:00.086   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:00.086 
00:00:00.086 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:00.086   Object <integer> = 0x0000000009976230 (160916016)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/0/] (level 3)
00:00:00.086   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.086   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:00.086   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.086   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/0/Config/] (level 4)
00:00:00.086   GuestCoreDumpDir <string>  = "/home/scott/.VirtualBox/Machines/minixp/Snapshots" (cb=50)
00:00:00.086   RamSize          <integer> = 0x000000001b400000 (457179136)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:00.086   Driver <string>  = "HGCM" (cb=5)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:00.086   Object <integer> = 0x00000000b72004a8 (3072328872)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:00.086   Driver <string>  = "MainStatus" (cb=11)
00:00:00.086 
00:00:00.086 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:00.086   First   <integer> = 0x0000000000000000 (0)
00:00:00.086   Last    <integer> = 0x0000000000000000 (0)
00:00:00.086   papLeds <integer> = 0x0000000009974968 (160909672)
00:00:00.086 
00:00:00.086 [/Devices/acpi/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/acpi/0/] (level 3)
00:00:00.086   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.086   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:00.086   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.086   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/acpi/0/Config/] (level 4)
00:00:00.086   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:00.086   FdcEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.086   HostBusPciAddress <integer> = 0x0000000000000000 (0)
00:00:00.086   HpetEnabled       <integer> = 0x0000000000000000 (0)
00:00:00.086   IOAPIC            <integer> = 0x0000000000000000 (0)
00:00:00.086   IocPciAddress     <integer> = 0x0000000000010000 (65536)
00:00:00.086   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:00.086   RamHoleSize       <integer> = 0x0000000020000000 (536870912)
00:00:00.086   RamSize           <integer> = 0x000000001b400000 (457179136)
00:00:00.086   ShowCpu           <integer> = 0x0000000000000000 (0)
00:00:00.086   ShowRtc           <integer> = 0x0000000000000000 (0)
00:00:00.086   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:00.086 
00:00:00.086 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:00.086   Driver <string>  = "ACPIHost" (cb=9)
00:00:00.086 
00:00:00.086 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:00.086 
00:00:00.086 [/Devices/apic/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/apic/0/] (level 3)
00:00:00.086   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/apic/0/Config/] (level 4)
00:00:00.086   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:00.086   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/e1000/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/i82078/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/i82078/0/] (level 3)
00:00:00.086   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/i82078/0/Config/] (level 4)
00:00:00.086   DMA       <integer> = 0x0000000000000002 (2)
00:00:00.086   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:00.086   IRQ       <integer> = 0x0000000000000006 (6)
00:00:00.086   MemMapped <integer> = 0x0000000000000000 (0)
00:00:00.086 
00:00:00.086 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:00.086   Driver <string>  = "Block" (cb=6)
00:00:00.086 
00:00:00.086 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:00.086   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.086   Type      <string>  = "Floppy 1.44" (cb=12)
00:00:00.086 
00:00:00.086 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:00.086   Driver <string>  = "MainStatus" (cb=11)
00:00:00.086 
00:00:00.086 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:00.086   First   <integer> = 0x0000000000000000 (0)
00:00:00.086   Last    <integer> = 0x0000000000000000 (0)
00:00:00.086   papLeds <integer> = 0x000000000997485c (160909404)
00:00:00.086 
00:00:00.086 [/Devices/i8254/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/i8254/0/] (level 3)
00:00:00.086 
00:00:00.086 [/Devices/i8254/0/Config/] (level 4)
00:00:00.086 
00:00:00.086 [/Devices/i8259/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/i8259/0/] (level 3)
00:00:00.086   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/i8259/0/Config/] (level 4)
00:00:00.086 
00:00:00.086 [/Devices/ichac97/] (level 2)
00:00:00.086 
00:00:00.086 [/Devices/ichac97/0/] (level 3)
00:00:00.086   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.086   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:00.086   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.086   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.086 
00:00:00.086 [/Devices/ichac97/0/Config/] (level 4)
00:00:00.086 
00:00:00.086 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:00.086   Driver <string>  = "AUDIO" (cb=6)
00:00:00.086 
00:00:00.086 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:00.086   AudioDriver <string>  = "pulse" (cb=6)
00:00:00.086   StreamName  <string>  = "minixp" (cb=7)
00:00:00.087 
00:00:00.087 [/Devices/mc146818/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/mc146818/0/] (level 3)
00:00:00.087 
00:00:00.087 [/Devices/mc146818/0/Config/] (level 4)
00:00:00.087   UseUTC <integer> = 0x0000000000000000 (0)
00:00:00.087 
00:00:00.087 [/Devices/parallel/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/pcarch/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/pcarch/0/] (level 3)
00:00:00.087   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/pcarch/0/Config/] (level 4)
00:00:00.087 
00:00:00.087 [/Devices/pcbios/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/pcbios/0/] (level 3)
00:00:00.087   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/pcbios/0/Config/] (level 4)
00:00:00.087   BootDevice0    <string>  = "FLOPPY" (cb=7)
00:00:00.087   BootDevice1    <string>  = "DVD" (cb=4)
00:00:00.087   BootDevice2    <string>  = "IDE" (cb=4)
00:00:00.087   BootDevice3    <string>  = "NONE" (cb=5)
00:00:00.087   FloppyDevice   <string>  = "i82078" (cb=7)
00:00:00.087   HardDiskDevice <string>  = "piix3ide" (cb=9)
00:00:00.087   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:00.087   LanBootRom     <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/PXE-Intel.rom" (cb=85)
00:00:00.087   McfgBase       <integer> = 0x0000000000000000 (0)
00:00:00.087   McfgLength     <integer> = 0x0000000000000000 (0)
00:00:00.087   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:00.087   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:00.087   RamHoleSize    <integer> = 0x0000000020000000 (536870912)
00:00:00.087   RamSize        <integer> = 0x000000001b400000 (457179136)
00:00:00.087   UUID           <bytes>   = "24 f1 41 f0 5e 47 40 4e 93 c5 23 99 90 6c b4 8b" (cb=16)
00:00:00.087 
00:00:00.087 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:00.087 
00:00:00.087 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:00.087   NIC           <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.087   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.087 
00:00:00.087 [/Devices/pci/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/pci/0/] (level 3)
00:00:00.087   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/pci/0/Config/] (level 4)
00:00:00.087   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/] (level 3)
00:00:00.087   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/Config/] (level 4)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:00.087   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.087   Driver <string>  = "MainKeyboard" (cb=13)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.087   Object <integer> = 0x000000000998e090 (161013904)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:00.087   QueueSize <integer> = 0x0000000000000040 (64)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:00.087   Driver <string>  = "MouseQueue" (cb=11)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:00.087   Driver <string>  = "MainMouse" (cb=10)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:00.087   Object <integer> = 0x0000000009974c20 (160910368)
00:00:00.087 
00:00:00.087 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:00.087   QueueSize <integer> = 0x0000000000000080 (128)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/0/] (level 3)
00:00:00.087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.087   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.087   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/0/Config/] (level 4)
00:00:00.087   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:00.087   CableConnected <integer> = 0x0000000000000001 (1)
00:00:00.087   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:00.087   MAC            <bytes>   = "08 00 27 71 64 dd" (cb=6)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:00.087   Driver <string>  = "IntNet" (cb=7)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:00.087   IgnoreConnectFailure <integer> = 0x0000000000000000 (0)
00:00:00.087   Network              <string>  = "HostInterfaceNetworking-eth2" (cb=29)
00:00:00.087   Trunk                <string>  = "eth2" (cb=5)
00:00:00.087   TrunkType            <integer> = 0x0000000000000003 (3)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:00.087   Driver <string>  = "MainStatus" (cb=11)
00:00:00.087 
00:00:00.087 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:00.087   papLeds <integer> = 0x0000000009974948 (160909640)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/] (level 3)
00:00:00.087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:00.087   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:00.087   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/Config/] (level 4)
00:00:00.087   Type <string>  = "PIIX4" (cb=6)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:00.087   Driver <string>  = "Block" (cb=6)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.087   Driver <string>  = "VD" (cb=3)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.087   Format <string>  = "VDI" (cb=4)
00:00:00.087   Path   <string>  = "/home/scott/.VirtualBox/HardDisks/minixp.vdi" (cb=45)
00:00:00.087   Type   <string>  = "HardDisk" (cb=9)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:00.087   Mountable <integer> = 0x0000000000000000 (0)
00:00:00.087   Type      <string>  = "HardDisk" (cb=9)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:00.087   Driver <string>  = "Block" (cb=6)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:00.087   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.087   Type      <string>  = "DVD" (cb=4)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:00.087   Driver <string>  = "MainStatus" (cb=11)
00:00:00.087 
00:00:00.087 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:00.087   First   <integer> = 0x0000000000000000 (0)
00:00:00.087   Last    <integer> = 0x0000000000000003 (3)
00:00:00.087   papLeds <integer> = 0x0000000009974860 (160909408)
00:00:00.087 
00:00:00.087 [/Devices/serial/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/0/] (level 3)
00:00:00.087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:00.087   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.087   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:00.087   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:00.087   Driver <string>  = "MainStatus" (cb=11)
00:00:00.087 
00:00:00.087 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:00.087   First   <integer> = 0x0000000000000000 (0)
00:00:00.087   Last    <integer> = 0x0000000000000000 (0)
00:00:00.087   papLeds <integer> = 0x0000000009974970 (160909680)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/0/] (level 3)
00:00:00.087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:00.087   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.087   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:00.087   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:00.087   Driver <string>  = "MainStatus" (cb=11)
00:00:00.087 
00:00:00.087 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:00.087   First   <integer> = 0x0000000000000000 (0)
00:00:00.087   Last    <integer> = 0x0000000000000000 (0)
00:00:00.087   papLeds <integer> = 0x000000000997496c (160909676)
00:00:00.087 
00:00:00.087 [/Devices/vga/] (level 2)
00:00:00.087 
00:00:00.087 [/Devices/vga/0/] (level 3)
00:00:00.087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:00.087   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:00.087   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.087   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/Devices/vga/0/Config/] (level 4)
00:00:00.087   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:00.087   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:00.087   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:00.087   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:00.087   LogoFile         <string>  = "" (cb=1)
00:00:00.087   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:00.087   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:00.087   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:00.087   VRamSize         <integer> = 0x0000000000c00000 (12582912)
00:00:00.087 
00:00:00.087 [/Devices/vga/0/LUN#0/] (level 4)
00:00:00.087   Driver <string>  = "MainDisplay" (cb=12)
00:00:00.087 
00:00:00.087 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:00.087   Object <integer> = 0x00000000099750b8 (160911544)
00:00:00.087 
00:00:00.087 [/Devices/virtio-net/] (level 2)
00:00:00.087 
00:00:00.087 [/HWVirtExt/] (level 1)
00:00:00.087   64bitEnabled       <integer> = 0x0000000000000000 (0)
00:00:00.087   EnableLargePages   <integer> = 0x0000000000000000 (0)
00:00:00.087   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:00.087   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:00.087   Enabled            <integer> = 0x0000000000000001 (1)
00:00:00.087   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:00.087 
00:00:00.087 [/MM/] (level 1)
00:00:00.087   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
00:00:00.087 
00:00:00.087 [/PDM/] (level 1)
00:00:00.087 
00:00:00.087 [/PDM/AsyncCompletion/] (level 2)
00:00:00.087 
00:00:00.087 [/PDM/AsyncCompletion/File/] (level 3)
00:00:00.087 
00:00:00.087 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:00.087 
00:00:00.087 [/PDM/BlkCache/] (level 2)
00:00:00.087   CacheSize <integer> = 0x0000000000500000 (5242880)
00:00:00.087 
00:00:00.087 [/PDM/Devices/] (level 2)
00:00:00.087 
00:00:00.087 [/PDM/Devices/VBoxEhci/] (level 3)
00:00:00.087   Path         <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxEhciR3.so" (cb=95)
00:00:00.087   R0SearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
00:00:00.087   RCSearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
00:00:00.087 
00:00:00.087 [/PDM/Drivers/] (level 2)
00:00:00.087 
00:00:00.087 [/PDM/Drivers/VBoxC/] (level 3)
00:00:00.087   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:00.087 
00:00:00.087 [/TM/] (level 1)
00:00:00.087   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:00.087 
00:00:00.087 [/USB/] (level 1)
00:00:00.087 
00:00:00.087 [/USB/USBProxy/] (level 2)
00:00:00.087 
00:00:00.087 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:00.087 
00:00:00.087 ********************* End of CFGM dump **********************
00:00:00.087 MM: cbHyperHeap=0x140000 (1310720)
00:00:00.088 Logical host processors: 2 present, 2 max, 2 online, online mask: 0000000000000003
00:00:00.088 ************************* CPUID dump ************************
00:00:00.088          RAW Standard CPUIDs
00:00:00.088      Function  eax      ebx      ecx      edx
00:00:00.088 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:00.088 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:00.088 Gst: 00000001  000006fb 00000800 00000209 078bf1bf
00:00:00.088 Hst:           000006fb 01020800 0000e3fd bfebfbff
00:00:00.088 Gst: 00000002  05b0b101 005657f0 00000000 2cb43049
00:00:00.088 Hst:           05b0b101 005657f0 00000000 2cb43049
00:00:00.088 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:00.088 Hst:           00000000 00000000 00000000 00000000
00:00:00.088 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:00.088 Hst:           04000121 01c0003f 0000003f 00000001
00:00:00.088 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:00.088 Hst:           00000040 00000040 00000003 00000220
00:00:00.088 Name:                            GenuineIntel
00:00:00.088 Supports:                        0-5
00:00:00.088 Family:                          6  	Extended: 0 	Effective: 6
00:00:00.088 Model:                           15  	Extended: 0 	Effective: 15
00:00:00.088 Stepping:                        11
00:00:00.088 Type:                            0 (primary)
00:00:00.088 APIC ID:                         0x00
00:00:00.088 Logical CPUs:                    0
00:00:00.088 CLFLUSH Size:                    8
00:00:00.088 Brand ID:                        0x00
00:00:00.088 Mnemonic - Description                 = guest (host)
00:00:00.088 FPU - x87 FPU on Chip                  = 1 (1)
00:00:00.088 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:00.088 DE - Debugging extensions              = 1 (1)
00:00:00.088 PSE - Page Size Extension              = 1 (1)
00:00:00.088 TSC - Time Stamp Counter               = 1 (1)
00:00:00.088 MSR - Model Specific Registers         = 1 (1)
00:00:00.088 PAE - Physical Address Extension       = 0 (1)
00:00:00.088 MCE - Machine Check Exception          = 1 (1)
00:00:00.088 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:00.088 APIC - APIC On-Chip                    = 0 (1)
00:00:00.088 10 - Reserved                          = 0 (0)
00:00:00.088 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:00.088 MTRR - Memory Type Range Registers     = 1 (1)
00:00:00.088 PGE - PTE Global Bit                   = 1 (1)
00:00:00.088 MCA - Machine Check Architecture       = 1 (1)
00:00:00.088 CMOV - Conditional Move Instructions   = 1 (1)
00:00:00.088 PAT - Page Attribute Table             = 1 (1)
00:00:00.088 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:00.088 PSN - Processor Serial Number          = 0 (0)
00:00:00.088 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:00.088 20 - Reserved                          = 0 (0)
00:00:00.088 DS - Debug Store                       = 0 (1)
00:00:00.088 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:00.088 MMX - Intel MMX Technology             = 1 (1)
00:00:00.088 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:00.088 SSE - SSE Support                      = 1 (1)
00:00:00.088 SSE2 - SSE2 Support                    = 1 (1)
00:00:00.088 SS - Self Snoop                        = 0 (1)
00:00:00.088 HTT - Hyper-Threading Technology       = 0 (1)
00:00:00.088 TM - Thermal Monitor                   = 0 (1)
00:00:00.088 30 - Reserved                          = 0 (0)
00:00:00.088 PBE - Pending Break Enable             = 0 (1)
00:00:00.088 Supports SSE3                          = 1 (1)
00:00:00.088 PCLMULQDQ                              = 0 (0)
00:00:00.088 DS Area 64-bit layout                  = 0 (1)
00:00:00.088 Supports MONITOR/MWAIT                 = 1 (1)
00:00:00.088 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:00.088 VMX - Virtual Machine Technology       = 0 (1)
00:00:00.088 SMX - Safer Mode Extensions            = 0 (1)
00:00:00.088 Enhanced SpeedStep Technology          = 0 (1)
00:00:00.088 Terminal Monitor 2                     = 0 (1)
00:00:00.088 Supplemental SSE3 instructions         = 1 (1)
00:00:00.088 L1 Context ID                          = 0 (0)
00:00:00.088 11 - Reserved                          = 0 (0)
00:00:00.088 FMA extensions using YMM state         = 0 (0)
00:00:00.088 CMPXCHG16B instruction                 = 0 (1)
00:00:00.088 xTPR Update Control                    = 0 (1)
00:00:00.088 Perf/Debug Capability MSR              = 0 (1)
00:00:00.088 16 - Reserved                          = 0 (0)
00:00:00.088 PCID - Process-context identifiers     = 0 (0)
00:00:00.088 DCA - Direct Cache Access              = 0 (0)
00:00:00.088 SSE4.1 instruction extensions          = 0 (0)
00:00:00.088 SSE4.2 instruction extensions          = 0 (0)
00:00:00.088 Supports the x2APIC extensions         = 0 (0)
00:00:00.088 MOVBE instruction                      = 0 (0)
00:00:00.088 POPCNT instruction                     = 0 (0)
00:00:00.088 TSC-Deadline LAPIC timer mode          = 0 (0)
00:00:00.088 AESNI instruction extensions           = 0 (0)
00:00:00.088 XSAVE/XRSTOR extended state feature    = 0 (0)
00:00:00.088 Supports OSXSAVE                       = 0 (0)
00:00:00.088 AVX instruction extensions             = 0 (0)
00:00:00.088 29/30 - Reserved                       = 0x0 (0x0)
00:00:00.088 31 - Reserved (always 0)               = 0 (0)
00:00:00.088 
00:00:00.088          RAW Extended CPUIDs
00:00:00.088      Function  eax      ebx      ecx      edx
00:00:00.088 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:00.088 Hst:           80000008 00000000 00000000 00000000
00:00:00.088 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:00.088 Hst:           00000000 00000000 00000001 20100000
00:00:00.088 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:00.088 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:00.088 Gst: 80000003  44203229 43206f75 20205550 45202020
00:00:00.088 Hst:           44203229 43206f75 20205550 45202020
00:00:00.088 Gst: 80000004  30353536 20402020 33332e32 007a4847
00:00:00.088 Hst:           30353536 20402020 33332e32 007a4847
00:00:00.088 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:00.088 Hst:           00000000 00000000 00000000 00000000
00:00:00.088 Gst: 80000006  00000000 00000000 10008040 00000000
00:00:00.088 Hst:           00000000 00000000 10008040 00000000
00:00:00.088 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:00.088 Hst:           00000000 00000000 00000000 00000000
00:00:00.088 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:00.088 Hst:           00003024 00000000 00000000 00000000
00:00:00.088 Gst: 80000009  07280202 00000000 00000000 00000503*
00:00:00.088 Hst:           07280202 00000000 00000000 00000503
00:00:00.088 Ext Name:                        
00:00:00.088 Ext Supports:                    0x80000000-0x80000008
00:00:00.088 Family:                          0  	Extended: 0 	Effective: 0
00:00:00.088 Model:                           0  	Extended: 0 	Effective: 0
00:00:00.088 Stepping:                        0
00:00:00.088 Brand ID:                        0x000
00:00:00.088 Mnemonic - Description                 = guest (host)
00:00:00.088 FPU - x87 FPU on Chip                  = 0 (0)
00:00:00.088 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:00.088 DE - Debugging extensions              = 0 (0)
00:00:00.088 PSE - Page Size Extension              = 0 (0)
00:00:00.088 TSC - Time Stamp Counter               = 0 (0)
00:00:00.088 MSR - K86 Model Specific Registers     = 0 (0)
00:00:00.088 PAE - Physical Address Extension       = 0 (0)
00:00:00.088 MCE - Machine Check Exception          = 0 (0)
00:00:00.088 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:00.088 APIC - APIC On-Chip                    = 0 (0)
00:00:00.088 10 - Reserved                          = 0 (0)
00:00:00.088 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:00.088 MTRR - Memory Type Range Registers     = 0 (0)
00:00:00.088 PGE - PTE Global Bit                   = 0 (0)
00:00:00.088 MCA - Machine Check Architecture       = 0 (0)
00:00:00.088 CMOV - Conditional Move Instructions   = 0 (0)
00:00:00.088 PAT - Page Attribute Table             = 0 (0)
00:00:00.088 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:00.088 18 - Reserved                          = 0 (0)
00:00:00.088 19 - Reserved                          = 0 (0)
00:00:00.088 NX - No-Execute Page Protection        = 0 (1)
00:00:00.088 DS - Debug Store                       = 0 (0)
00:00:00.088 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:00.088 MMX - Intel MMX Technology             = 0 (0)
00:00:00.088 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:00.088 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:00.088 26 - 1 GB large page support           = 0 (0)
00:00:00.088 27 - RDTSCP instruction                = 0 (0)
00:00:00.088 28 - Reserved                          = 0 (0)
00:00:00.088 29 - AMD Long Mode                     = 0 (1)
00:00:00.088 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:00.088 31 - AMD 3DNow                         = 0 (0)
00:00:00.088 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:00.088 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:00.088 SVM - AMD VM Extensions                = 0 (0)
00:00:00.088 APIC registers starting at 0x400       = 0 (0)
00:00:00.088 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:00.088 Advanced bit manipulation              = 0 (0)
00:00:00.088 SSE4A instruction support              = 0 (0)
00:00:00.088 Misaligned SSE mode                    = 0 (0)
00:00:00.088 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:00.088 OS visible workaround                  = 0 (0)
00:00:00.088 Instruction based sampling             = 0 (0)
00:00:00.088 SSE5 support                           = 0 (0)
00:00:00.088 SKINIT, STGI, and DEV support          = 0 (0)
00:00:00.088 Watchdog timer support.                = 0 (0)
00:00:00.088 31:14 - Reserved                       = 0x0 (0x0)
00:00:00.088 Full Name:                       Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
00:00:00.088 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:00.088 TLB 2/4M Data:                   res0     0 entries
00:00:00.088 TLB 4K Instr/Uni:                res0     0 entries
00:00:00.088 TLB 4K Data:                     res0     0 entries
00:00:00.088 L1 Instr Cache Line Size:        0 bytes
00:00:00.088 L1 Instr Cache Lines Per Tag:    0
00:00:00.088 L1 Instr Cache Associativity:    res0  
00:00:00.088 L1 Instr Cache Size:             0 KB
00:00:00.088 L1 Data Cache Line Size:         0 bytes
00:00:00.088 L1 Data Cache Lines Per Tag:     0
00:00:00.088 L1 Data Cache Associativity:     res0  
00:00:00.088 L1 Data Cache Size:              0 KB
00:00:00.088 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:00.088 L2 TLB 2/4M Data:                off       0 entries
00:00:00.088 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:00.088 L2 TLB 4K Data:                  off       0 entries
00:00:00.088 L2 Cache Line Size:              0 bytes
00:00:00.088 L2 Cache Lines Per Tag:          0
00:00:00.088 L2 Cache Associativity:          off   
00:00:00.088 L2 Cache Size:                   0 KB
00:00:00.088 APM Features:                   
00:00:00.088 Physical Address Width:          36 bits
00:00:00.088 Virtual Address Width:           48 bits
00:00:00.088 Guest Physical Address Width:    0 bits
00:00:00.088 Physical Core Count:             0
00:00:00.088 
00:00:00.088          RAW Centaur CPUIDs
00:00:00.088      Function  eax      ebx      ecx      edx
00:00:00.088 Gst: c0000000  07280202 00000000 00000000 00000503
00:00:00.088 Hst:           07280202 00000000 00000000 00000503
00:00:00.088 Gst: c0000001  07280202 00000000 00000000 00000503
00:00:00.088 Hst:           07280202 00000000 00000000 00000503
00:00:00.088 Gst: c0000002  07280202 00000000 00000000 00000503
00:00:00.088 Hst:           07280202 00000000 00000000 00000503
00:00:00.088 Gst: c0000003  07280202 00000000 00000000 00000503
00:00:00.088 Hst:           07280202 00000000 00000000 00000503
00:00:00.088 Centaur Supports:                0xc0000000-0x07280202
00:00:00.088 Mnemonic - Description                 = guest (host)
00:00:00.088 AIS - Alternate Instruction Set        = 0 (1)
00:00:00.088 AIS-E - AIS enabled                    = 0 (1)
00:00:00.088 RNG - Random Number Generator          = 0 (0)
00:00:00.088 RNG-E - RNG enabled                    = 0 (0)
00:00:00.088 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:00.088 FEMMS - FEMMS                          = 0 (0)
00:00:00.088 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:00.088 ACE-E - ACE enabled                    = 0 (0)
00:00:00.088 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
00:00:00.088 ACE2-E - ACE enabled                   = 0 (0)
00:00:00.088 PHE - Hash Engine                      = 0 (1)
00:00:00.088 PHE-E - PHE enabled                    = 0 (0)
00:00:00.088 PMM - Montgomery Multiplier            = 0 (0)
00:00:00.088 PMM-E - PMM enabled                    = 0 (0)
00:00:00.088 
00:00:00.088 
00:00:00.088 ******************** End of CPUID dump **********************
00:00:00.088 pgmR3PoolInit: cMaxPages=0x400 cMaxUsers=0x800 cMaxPhysExts=0x800 fCacheEnable=true 
00:00:00.089 REM: VBoxREM32
00:00:00.092 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:00.124 TM: cTSCTicksPerSecond=0xcfabc2bb (3 484 140 219) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:00.124 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:00.124 CoreCode: R3=008ca000 R0=f8b3e000 RC=a035a000 Phys=0000000025f10000 cb=0x3000
00:00:00.125 AIOMgr: Default manager type is "Async"
00:00:00.125 AIOMgr: Default file backend is "NonBuffered"
00:00:00.125 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
00:00:00.125 BlkCache: Cache commit interval is 10000 ms
00:00:00.125 BlkCache: Cache commit threshold is 2621440 bytes
00:00:00.127 [SMP] BIOS with 1 CPUs
00:00:00.135 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf8b89020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.139 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf8bc0020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.139 Activating Local APIC
00:00:00.139 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:00.139 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:00.139 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.140 Shared Folders service loaded.
00:00:00.143 DrvBlock: Flushes will be ignored
00:00:00.143 DrvBlock: Async flushes will be passed to the disk
00:00:00.144 DrvBlock: Flushes will be ignored
00:00:00.144 DrvBlock: Async flushes will be passed to the disk
00:00:00.144 VDInit finished
00:00:00.144 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 20971520
00:00:00.144 PIIX3 ATA: LUN#1: no unit
00:00:00.144 DrvBlock: Flushes will be ignored
00:00:00.144 DrvBlock: Async flushes will be passed to the disk
00:00:00.144 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:00.144 PIIX3 ATA: LUN#3: no unit
00:00:00.144 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.144 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.144 IntNet#0: szNetwork={HostInterfaceNetworking-eth2} enmTrunkType=3 szTrunk={eth2} fFlags=0x0 cbRecv=325632 cbSend=196608
00:00:00.144 Audio: Trying driver 'pulse'.
00:00:00.149 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:00.149 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:00.149 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
00:00:00.164 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
00:00:00.164 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:00.164 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
00:00:00.164 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
00:00:00.165 SUP: Loaded VBoxEhciR0.r0 (/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxEhciR0.r0) at 0xf8c6c020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.165 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:00.165 PGM: The CPU physical address width is 36 bits
00:00:00.165 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:00.178 VMM: fUsePeriodicPreemptionTimers=true 
00:00:00.178 HWACCM: Host CR4=000006D0
00:00:00.178 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:00.178 HWACCM: MSR_IA32_VMX_BASIC_INFO       = 5a08000000000b
00:00:00.178 HWACCM: VMCS id                       = b
00:00:00.178 HWACCM: VMCS size                     = 800
00:00:00.178 HWACCM: VMCS physical address limit   = None
00:00:00.178 HWACCM: VMCS memory type              = 6
00:00:00.178 HWACCM: Dual monitor treatment        = 1
00:00:00.178 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 3f00000016
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_VIRTUAL_NMI
00:00:00.178 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = f7f9fffe0401e172
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_NMI_WINDOW_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:00.178 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = 100000000
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:00.178 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = 1fff000011ff
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:00.178 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 3efff00036dff
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:00.178 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:00.178 HWACCM: MSR_IA32_VMX_MISC             = 403c0
00:00:00.178 HWACCM:    MSR_IA32_VMX_MISC_PREEMPT_TSC_BIT 0
00:00:00.178 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:00.178 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:00.178 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:00.178 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:00.178 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:00.178 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:00.178 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:00.178 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 67ff
00:00:00.178 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2c
00:00:00.178 HWACCM: TPR shadow physaddr           = 00000000357d9000
00:00:00.178 HWACCM: VCPU0: MSR bitmap physaddr      = 0000000035715000
00:00:00.178 HWACCM: VCPU0: VMCS physaddr            = 00000000357f7000
00:00:00.178 HWACCM: Real Mode TSS guest physaddr  = 00000000f0800000
00:00:00.178 HWACCM: Non-Paging Mode EPT CR3       = 00000000f0803000
00:00:00.178 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:00.178 HWACCM: 32-bit guests supported.
00:00:00.178 HWACCM: VMX enabled!
00:00:00.178 HWACCM: TPR Patching disabled.
00:00:00.178 HWACCM:    VT-x/AMD-V init method: GLOBAL
00:00:00.185 VM: Halt method global1 (5)
00:00:00.185 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=2000
00:00:00.185 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:00.186 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:00.186 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:00.189 Guest Log: BIOS: VirtualBox 4.0.2
00:00:00.189 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.239 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.239 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.239 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:00.239 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.239 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.240 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:00.254 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=012e5000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:02.714 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:02.717 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:02.718 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:02.718 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:02.718 Guest Log: BIOS: Boot from CD-ROM failed
00:00:02.718 Guest Log: BIOS: Booting from Hard Disk...
00:00:04.354 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:04.434 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=012e5000 w=640 h=480 bpp=0 cbLine=0x140, flags=0x1
00:00:06.050 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xef (-1 usec ago)
00:00:06.050 PIIX3 ATA: LUN#0: aborting current command
00:00:07.541 EHCI: Hardware reset
00:00:07.541 EHCI: USB Operational
00:00:07.735 OHCI: Software reset
00:00:07.735 OHCI: USB Reset
00:00:07.735 OHCI: USB Operational
00:00:07.740 PCNet#0: Init: ss32=1 GCRDRA=0x03e2c420[64] GCTDRA=0x03e2c020[64]
00:00:08.803 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:08.804 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:09.164 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=012e5000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:09.205 PCNet#0: Init: ss32=1 GCRDRA=0x03e2c420[64] GCTDRA=0x03e2c020[64]
00:00:09.206 PCNet#0: Init: ss32=1 GCRDRA=0x03e2c420[64] GCTDRA=0x03e2c020[64]
00:00:09.604 EHCI: USB Suspended
00:00:09.794 OHCI: USB Suspended
00:00:10.014 PCNet#0: Init: ss32=1 GCRDRA=0x03e2c420[64] GCTDRA=0x03e2c020[64]
00:00:11.981 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:11.981 Audio: set_record_source ars=0 als=0 (not implemented)
00:05:55.362 Changing the VM state from 'RUNNING' to 'SUSPENDING'.
00:05:55.435 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.

```

---

### Post by sdowney717 on 2011-02-11
I had no way of interacting with the VM, so I cntrl-c the terminal window to abort the machine

---

### Post by phoenix122 on 2011-02-12
> **sdowney717 said:**
> works and yet does not work
screenshot show that headless process starts.
in the VM manager gui, it shows the vm running
BUT, I never get the window box of the machine

terminal output. I saved the batch file as vbox.sh and made it executable

```
Virtual Machine Menu

1 - Start a Virtual Machine with default options
2 - Change default options
3 - View current Virtual Machines

0 - Exit

Enter selection: 1
Currently Available Virtual Machines

     1	"mythbuntu" 
     2	"mythdownload" 
     3	"minixp" 
     4	"xppro32" 
     5	"haiku" 
     6	"xppro322" 
Please make a selection, select q to quit: 3




Starting "minixp"  Machine
Oracle VM VirtualBox Headless Interface 4.0.2
(C) 2008-2011 Oracle Corporation
All rights reserved.




```

That's because its not meant to display any window. I like to be able to use my VM's from any computer in the house, and except when i'm doing an initial install, i use ssh to log in.(it helps with my pathetic command line-fu :))

Taken from the VirtualBox User Manual:

> 
While any VM started from the VirtualBox Manager is capable of running virtual machines remotely, it is not convenient to have to run the full-fledged GUI if you never want to have VMs displayed locally in the first place...if you are running server hardware whose only purpose is to host VMs, and all your VMs are supposed to run remotely over VRDP, then it is pointless to have a graphical user interface on the server at all...VirtualBox therefore comes with yet another front-end called VBoxHeadless, which produces no visible output on the host at all, but instead only delivers VRDP data.


This version will just show the regular VM window when you select an option.

 
  
```
#!/bin/bash
#######################
# Author:phoenix122
# Version:1.0
#######################  
# Turn on extended pattern matching 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################
# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform program exit housekeeping
	# Optionally accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}

function error_exit 
{
	# Display error message and exit
	echo ""
	echo "${PROGNAME}: ${1:-"Unknown Error"}" 1>&2
	clean_up 1
}

 function press_enter 
{
	echo ""
	echo -n "Press Enter to continue"
	read
	clear
}

function list_vm 
{   #uncomment to hide Virtual Machine UUID 
	echo "" "Virtual Machine Info:"
    VBoxManage --nologo list vms | nl #| sed -e 's/{.*}//g'
	
}
#############################################################
# Main Functions for starting a VM

function vm_starter
{   
	#Edits the output to remove the UUID and redirect the output
	VBoxManage --nologo list vms | sed -e 's/{.*}//g' > $TEMP_FILE
	# Re-run command, cut the Machine Name, braces, and whitespace, 
	# This goes into a different tempfile and user choice is taken from it
	VBoxManage --nologo list vms \
	| sed -e 's/".*"//g;s/[}]//;s/[{]//;s/^[ \t]*//;s/[ \t]*$//' > $TEMP_FILE2

	while [[ 1 ]] ; do
		echo "Currently Available Virtual Machines"
		echo ""
		cat -n "$TEMP_FILE"
		nr=$( cat "${TEMP_FILE}" | wc -l )
		read -p "Please make a selection, select q to quit: " choice
		case $choice in
			# Check for digits
			+([0-9])) do_action ;;
			q|Q) clear ; break ;;
			*) echo "Invalid choice" ; press_enter ;;
    	esac
done
}

function do_action
{
	runline=$(sed -n "$choice""p" "$TEMP_FILE2")
	line=$(sed -n "$choice""p" "$TEMP_FILE") 
	clear ; echo "" 
	echo "Starting $line Machine"
	echo ""
	VBoxManage startvm --type gui "$runline" 
}

#############################################################
#############################################################

if [ -d ~/tmp ]; then
	TEMP_DIR=~/tmp
else
	TEMP_DIR=/tmp
fi

selection= 
vrde="--vrde off" 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ "$selection" = "0" ]; do
    echo "Virtual Machine Menu"
	echo ""
    echo "1 - Start a Virtual Machine"
	echo "2 - View currently registered Virtual Machines"
	echo ""
    echo "0 - Exit"
	echo ""
    echo -n "Enter selection: "
    read selection
    echo ""
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) list_vm ; press_enter ;; 
		0 ) clear ; clean_up ; exit ;;
		* ) echo "Please enter 1, 2, or 0"
    esac
done

```

---

### Post by sdowney717 on 2011-02-12
I just tried it and this one loads a terminal window which is instantly 
terminated, so it will flash up on the screen and in a flash is gone again.
Did this by simply clicking on it and selecting run in a terminal window

however, it does run if you load it from terminal itself
I think it should be designed to run just by a click from the gui.
otherwise, you have to go to terminal, cd to the Desktop, and type ./nameoffile.sh

I have a simple shell script I wrote that you can simply click on and have it run without disappearing. it does disappear after it terminates, so maybe the process takes so long it stays on the screen.

> gksudo /etc/init.d/libvirt-bin stop
sudo modprobe -r kvm_intel
sudo modprobe -r kvm


gksu /etc/init.d/vboxdrv.dpkg-dist setup



a year ago, I was playing with kvm, and now if i reboot, in order to start a vm with vbox, I must run this script and have it redo the setup. 
dkms is not doing its job for me. but that is unrelated to the idea of clicking and having the terminal stay up.

---

### Post by sdowney717 on 2011-02-12
how are you ssh ing into your box from another machine?
I would like to see that.
can you share the steps to do this?

---

### Post by phoenix122 on 2011-02-12
> **sdowney717 said:**
> I just tried it and this one loads a terminal window which is instantly 
terminated, so it will flash up on the screen and in a flash is gone again.
Did this by simply clicking on it and selecting run in a terminal window

however, it does run if you load it from terminal itself
I think it should be designed to run just by a click from the gui.
otherwise, you have to go to terminal, cd to the Desktop, and type ./nameoffile.sh

](*,)hmm, gotta admit i'm stumped. I'm able to run it from my desktop with no problems. it loads a window and acts just as if i ran it straight from the terminal. I installed VirtualBox on another PC (Ubuntu 10.04 x64) and used the same script, and got the same results.

---

### Post by phoenix122 on 2011-02-12
> **sdowney717 said:**
> how are you ssh ing into your box from another machine?
I would like to see that.
can you share the steps to do this?

1. Install the SSH server on the machine you want to control
```

sudo apt-get install openssh-server

```

2.(Optional) By default, ssh listens on port 22. If you want to change it, edit the config file (replace nano with your favorite text editor)

```

sudo nano /etc/ssh/sshd_config

```

3. from another machine, try and login. (I use PuTTy, but you can do it from the terminal as well)
Terminal: 
```

ssh IP_ADDRESS -p PORT -l USER_NAME

```

Hope this helps!

---

### Post by sdowney717 on 2011-02-12
interesting, so could I use a windows PC to ssh into a ubuntu PC and the VM shows up on the windows PC?

---

### Post by sdowney717 on 2011-02-12
I uploaded my vbox.sh file.
Can you try it and see if it runs just by clicking on it or does it flash on the screen and vanish.

---

### Post by phoenix122 on 2011-02-12
I took a look. there was an empty line at the top of the script. thats what caused it not to run. 

open up the script and get rid of that empty line at the top. then you should have no problems.

---

### Post by phoenix122 on 2011-02-12
> **sdowney717 said:**
> interesting, so could I use a windows PC to ssh into a ubuntu PC and the VM shows up on the windows PC?

if you use ssh, you'll get a terminal prompt for your vm. 
the first screenshot shows what i mean. (I used PuTTY to ssh into a Debian VM)

if you want to see a desktop, then you would have to use 
Remote Desktop on your win PC. (The second Screenshot is me logging into to a Win VM)

---

### Post by sdowney717 on 2011-02-12
Yes, thanks that makes it work.
So can you ssh across the net?
I will give this a try someday.

---

### Post by phoenix122 on 2011-02-12
yep. here's a link (Windows using Cygwin)

[personal home ssh server]("http://lifehacker.com/#!205090/geek-to-live--set-up-a-personal-home-ssh-server")

I've never done it on Ubuntu yet, but it shouldn't be that hard

---

