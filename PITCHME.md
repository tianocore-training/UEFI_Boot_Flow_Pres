---?image=assets/images/gitpitch-audience.jpg
@title[UEFI Foot Flow & Overview]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI and Platform Initialization (PI) Boot Flow & Overview 

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Boot flow and Overview

  Copyright (c) 2019, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Review PI and UEFI Boot Process  </span><br><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Answer <a href='https://github.com/tianocore/tianocore.github.io/wiki/UEFI%20EDKII%20Learning%20Dev'>web-based training</a> related questions </span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Answer: Where does Intel® FSP Fit? </span> <br><br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;What’s new in UEFI.org</span> 


---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Boot Flow Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Where is the Firmware</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Where is the UEFI Firmware on a platform</span>


---?image=/assets/images/slides/Slide4_2.JPG
@title[UEFI Boot Flow]
<p align="right"><span class="gold" >@size[01.1em](<b>Firmware is Everywhere</b>) </span></p>
@snap[north-east span-50 ]
<br>
<p style="line-height:50%" >&nbsp;</p>
@box[bg-navy text-white ](<p style="line-height:70%" ><span style="font-size:0.9em; font-weight: bold;" ><br><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
<br>
@snapend

@snap[north-east span-50 fragment]
<br>
<p style="line-height:50%" ><br>&nbsp;</p>
<ul style="list-style-type:disc; line-height:0.7;">
 <li><span style="font-size:0.65em">GBe NIC, WiFi, Bluetooth, WiGig </span></li>
 <li><span style="font-size:0.65em">Baseband (3G, LTE) Modems </span></li>
 <li><span style="font-size:0.65em">Sensor Hubs </span></li>
 <li><span style="font-size:0.65em">NFC, GPS Controllers </span></li>
 <li><span style="font-size:0.65em">HDD/SSD </span></li>
 <li><span style="font-size:0.65em">Keyboard  Embedded Controllers </span></li>
 <li><span style="font-size:0.65em">Battery Gauge </span></li>
 <li><span style="font-size:0.65em">Baseboard Management Controllers (BMC) </span></li>
 <li><span style="font-size:0.65em">Graphics/Video </span></li>
 <li><span style="font-size:0.65em">USB Thumb Drives, keyboards/mice </span></li>
 <li><span style="font-size:0.65em">Chargers, adapters </span></li>
 <li><span style="font-size:0.65em">TPM, security co-processors </span></li>
 <li><span style="font-size:0.65em">Routers, network appliances </span></li>
</ul>
<br>
@snapend

@snap[north-west span-100 fragment]
<br>
<br>
<br>
<br>
<p style="line-height:20%" ><br><br>&nbsp;</p>
<p style="line-height:20%"  align="left">
&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br>
@fa[haykal gp-bullet-magenta]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br>
<br>&nbsp;@fa[haykal gp-bullet-magenta]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br><br>
&nbsp;&nbsp;@fa[haykal gp-bullet-magenta]<br>
</p>
@snapend




@snap[south-west span-45 fragment]
<p align="right">@fa[haykal gp-bullet-magenta]</p>
<p style="line-height:20%" ><br>&nbsp;</p>
@snapend

@snap[south-east span-50 fragment]
@box[bg-royal text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:0.8em; font-weight: bold;" >Main system firmware &lpar;BIOS, UEFI firmware, coreboot&rpar;<br>&nbsp;</span></p>)
@snapend

Note:
### BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  GBe - Gigabit Network Interface controller
  NFC   Near Field Communication
  GPS	Global Positioning System
  HDD/SSD Hard Drive - Solid State Drive
  TPM    Trusted Platform Module

Image source: http://www.tweaktown.com/reviews/7497/tyan-s7076-intel-c612-server-motherboard-review/index3.html

+++?image=/assets/images/slides/Slide4_2.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow]
<p align="right"><span class="gold" >@size[01.1em](<b>Firmware is Everywhere</b>) </span></p>



@snap[south-west span-50 ]
<p align="right">@fa[haykal fa-2x gp-bullet-magenta]</p>
@snapend

@snap[south-east span-50 ]
@box[bg-royal text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:0.8em; font-weight: bold;" ><br>Main system firmware &lpar;BIOS, UEFI firmware, coreboot&rpar;<br><br>&nbsp;</span></p>)
<br>
<br>
<br>
<br>
<br>
@snapend

Note:
### BLOCK Diagram of a Platform
- We see that Firmware is everywher
- GBe NIC, WiFi, Bluetooth, WiGig
- Baseband (3G, LTE) Modems
- Sensor Hubs
- NFC, GPS Controllers
- HDD/SSD
- Keyboard and Embedded Controllers
- Battery Gauge
- Baseboard Management Controllers (BMC)
- Graphics/Video
- USB Thumb Drives, keyboards/mice
- Chargers, adapters
- TPM, security coprocessors
- Routers, network appliances
- Main system firmware (BIOS, UEFI firmware, coreboot)

  GBe - Gigabit Network Interface controller
  NFC   Near Field Communication
  GPS	Global Positioning System
  HDD/SSD Hard Drive - Solid State Drive
  TPM    Trusted Platform Module

Image source: http://www.tweaktown.com/reviews/7497/tyan-s7076-intel-c612-server-motherboard-review/index3.html




---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Boot Flow Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Boot Execution Flow</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Starting at the processor reset vector</span>


---?image=/assets/images/slides/Slide4.JPG
@title[UEFI Boot Flow]
### <p align="center"><span class="gold" >UEFI - PI & EDK II Boot Flow </span></p>
<br><br><br><br><br><br><br><br><br><br><br><br>
<p align="center"><span style="font-size:0.6em" ><b>The folloiwng Slides show UEFI  and Platform Initialziation (PI) Boot Execution Flow</b></span></p>

Note:
The next set of slides will detail the phases of the boot execution flow for UEFI

---?image=/assets/images/slides/Slide5.JPG
<!-- .slide: data-transition="none" -->		 
@title[UEFI Boot Flow Sec]
#### <p align="center"><span class="gold" > UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>SEC</b> </span></p>

Note:
SEC Function <Br>
          Consumes the Reset vector on IA
Serving as the root of trust in the system
Initial code that takes control of the system
May choose to authenticate the PEI Foundation 

+++?image=/assets/images/slides/Slide9_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[SEC - Pre-Memory Init ]
<p align="right"><span class="gold" >@size[1.1em](<b>Pre-Memory Initialization </b>)</span></p>
<p align="left">
<span style="font-size:0.8em" >Address Space</span></p>

Note:
- Until memory is initialized the address space is the same mapped to th 4GB address space in 32bit flat mode
- No-evection mode or Cache as Ram (CAR) is used for the Temporary memory



+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[SEC - characteristics ]
#### <p align="right"><span class="gold" >Starting at the reset vector </span></p>

The Processor Executes SEC starting at the first fetch from the reset vector 

- SEC Consumes the Reset vector 
- Serving as the root of trust 
- May choose to authenticate the PEI Foundation
- Init the APs waking stub
- Early microcode update
- Collect BIST (Built-in Self Test)
- Other charactistics of SEC   
    - Executed in place from flash
    - Written in assembly (16-bit & 32-bit) on Intel Architecuture	- 
Note:
SEC Function <Br>
          Consumes the Reset vector on IA
Serving as the root of trust in the system
Initial code that takes control of the system
May choose to authenticate the PEI Foundation 

Switch to 32-bit flat mode
Initialize the Boot strap processor BSP
Initialize PEI temporary memory NEM / CAR
Transfer control to PEI Core

SEC will have Platform specific functions
- AP waking stub
- Early microcode update
- Collect BIST (Built-in Self Test)
- Other charactistics of SEC   
  - Executed in place from flash
  - Written in assembly (16-bit & 32-bit)
+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[SEC - Firmware Terms ]
#### <p align="right"><span class="gold" >Terms to know about the Flash Device </span></p>
- Firmware Volume (FV) 
  - The basic storage with a firmware device
- Firmware File System (FFS)
  - Describes the organization of files within a FV

Note:
-A Firmware Volume (FV) is a logical firmware device. The basic storage <br>
repository for data and/or code is the firmware volume. Each firmware volume is organized into a
file system. As such, the file is the base unit of storage for firmware

-Firmware Volume (FV) <br>
A firmware file system (FFS) describes the organization of files and (optionally) free space within
the firmware volume. Each firmware file system has a unique GUID, which is used by the firmware
to associate a driver with a newly exposed firmware volume

---?image=/assets/images/slides/Slide6.JPG
<!-- .slide: data-transition="none" -->		 
@title[UEFI Boot Flow PEI]
#### <p align="center"><span class="gold"  >UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>PEI</b> </span></p>


Note:
PEI Function <Br>
- PEI Primary goals:
  -	Discover boot mode (Normal, S3, Recovery)
  - Discover and initialize some RAM that won’t be reconfigured
  -	Discover location of FV(s) containing DXE Core & Architecture Protocols and Launch DXE core

- PEI Phases – 
   - Pre – memory Init
   - Memory reference code (MRC)
   - Post Memory Init

Components: 
- Binaries: PEI Core and PEI Modules (PEIMs)
PEIMs are modules scheduled by the PEI core in the early phase of platform initialization. PEIMs are typically executed in place before system memory is available. 
- On IA running in No Eviction mode (NEM) aka.  Cache as RAM

Interfaces: Methods of Inter-PEIM communication
Core set of services (PeiServices), PEIM to PEIM Interfaces (PPIs), and simple Notifies (no timer in PEI)



---?image=/assets/images/slides/Slide7.JPG
<!-- .slide: data-transition="none" -->		 
@title[UEFI Boot Flow PEI-DXEIPL  & Hobs ]
#### <p align="center"><span class="gold"  >UEFI - PI & EDK II Boot Flow </span><span style="color:white;">-&nbsp;<b>DXEIPL</b> </span></p>

Note:
PEI - Hobs <Br>
Transition to DXE :
- HOBS  – a series of data structures in memory, created during PEI, that describe platform features, configuration, or data. HOBs are produced during PEI, and read-only during DXE (consumer). 

+++

@title[UEFI Boot Flow PEI-DXEIPL ]
#### <p align="center"><span class="gold"   >DXE IPL Characteristics   </span>
- No hard coded addresses allowed
- Find Largest Physical Memory HOB
   - Ideally this should be near Top Of Memory (TOM)
   - Allocate DXE Stack from Top of Memory
- Build HOB that describes DXE Stack
- Search FVs from HOB List for DXE Core
- Load DXE Core into Memory (PE/COFF)
- Build HOB that describes DXE Core
- Switch Stacks and Handoff to DXE Core

Note:


---?image=/assets/images/slides/Slide8.JPG
<!-- .slide: data-transition="none" -->		 

@title[UEFI Boot Flow DXE]
#### <p align="center"><span class="gold"   >UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>DXE</b> </span></p>


Note:
DXE <Br>

Works after system memory has been discovered and initialized
DXE drivers are typically stored in flash in compressed form and must be decompressed into memory before execution


+++
@title[DXE Characteristics]
#### <p align="right"><span class="gold"   >DXE Characteristics & Responsibilities  </span></p>
- Consumes HOB List from PEI
- Builds UEFI and DXE Service Tables  
- EFI System Table
- UEFI Boot Services Table & UEFI Runtime Services Table
- Hands off control to the DXE Dispatcher
- and more  . . . 
	

Note:
DXE Characteristics
- Consumes HOB List from PEI
- Builds UEFI and DXE Service Tables  
- EFI System Table
- UEFI Boot Services Table & UEFI Runtime Services Table
- DXE Services Table
- Makes Memory-Only Boot Services Available that will be in memory until ExitBootServices()
- Hands off control to the DXE Dispatcher
- Requires access to Firmware Volumes
- Requires LoadImage(), StartImage(), Exit()
- DXE Drivers will build the Architectural Protocols
- May require decompression service
 
- DXE FOUNDATION Theory of Operation
- The First goal is to Initialize the Platform – Initialize the Chipset and the platform 

- We want to Load Drivers to construct an environment that can support boot manager and  boot the OS 

---?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-transition="none" -->		 
@title[UEFI Boot Flow DXE]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>DXE</b> </span></p>


Note:
DXE - EFI System Table<Br>   
UEFI system table passed into your driver

It contains a pointer the System Configuration table  - This is an array of GUID Pointer pairs -  you can see the DXE Services table – The HOBs so for example if you have a PEIM that produces some data –and produces a GUIDed HOB this is how you would get the pointer to that HOBs – other examples 

The UEFI System table also has fields in it that point to the active consoles  - Input Console – Output Console – These would be used for the “Printf” i.e. Debug mechanism you  can use the Error console 
 UEFI Boot Services Table – we will go through these – this is boot services and goes away once the OS is booted so 
The Handle database  - that is maintained by the dxe core – The handle data base contains all the pointers to all the protocols that all the drivers produce. 

There are some protocols and handler services that if you have a DXE Driver that produces a  Protocol and that protocol needs to be accessed by other drivers than this is the mechanism to access other protocols – it is a boot services to access protocols thus you know to go to the boot services table definition and look at the boot services available to find which protocol you need or which protocol you need to produce.

The next table pointed to by the UEFI system services table is the UEFI Runtime Services Table – With these services you can access services to variables to read/write – access the real time clock – 
Run time services have to persist after the OS runtime and these services are still available.
The system configuration table you can see is still available even after the OS boots. 
However, recall that these are an array of GUID pointer pairs and that the GUID – so the GUID and pointer will persist but if you have a dependency of those GUIDS back into the  DXE boot services table it will not be valid at Runtime.  

Some additional fields VERSION Information – (not services specifically) – Information that is maintained during Runtime

Summary -
So that is how the UEFI system table points to many different Services and Data structures within the Firmware – and will be used by your drivers

The DXE core produces the UEFI System Table, and the UEFI System Table is used by every DXE driver and executable image invoked later on in the BDS phase. It contains all the information needed to utilize the services provided by the DXE core, and the services provided by any previously loaded DXE driver.
The DXE core produces the UEFI Boot Services, UEFI Runtime Services, and DXE Services using the architectural protocols that was produced by the DXE drivers. The UEFI System Table provides access to all the active console devices in the platform.  It provides access to UEFI Configuration Tables. The UEFI Configuration Tables contains more tables such as DXE Services, HOB List, ACPI, SMBIOS, and the SAL System Table. This list can also be expanded in the future.
Also included, is the handle database. Any executable image can access the handle database for any of the protocol interfaces that have been registered by DXE drivers. 
When the transition to the OS runtime is performed, the handle database, active consoles, UEFI Boot Services, and services provided by boot service DXE drivers are terminated. This frees up more memory for use by the OS, and leaves the UEFI System Table, UEFI Runtime Services Table, and the system configuration tables available in the OS runtime environment. 
There is also the option of converting all of the UEFI Runtime Services from a physical address space to an OS-specific virtual address space. This address space conversion may only be performed once. 

Let’s take a quick look at the end product of Framework—the tables that Framework will create for UEFI aware Operating systems.   They are implemented by the drivers dispatched during the DXE phase.  As specified by the UEFI spec, there are boot-time services and runtime services.  There is a handle database and a list of all the protocols that these handles have associated with them.  Of course, keep in mind that all these will be gone from memory when the OS has booted.  The only things that will remain are the runtime services.

+++?image=/assets/images/slides/Slide10.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow EFI System Table]
#### <p align="center"><span class="gold">UEFI System Table </span>

Note:
DXE - EFI System Table<Br>   
Created in DXE and is the pointer to everything in the system

---?image=/assets/images/slides/Slide11.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow DXE- UEFI Drivers]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;-&nbsp;<b>DXE UEFI</b> </span></p>


Note:
DXE - UEFI Drivers<Br>
- Characteristics :
- UEFI drivers with  do not have dependency so are dispatched last Enhance

- What do UEFI Drivers do?
- UEFI Drivers extend firmware
- Add support for new hardware
- No HW dependence
- No OS dependence
- Portable across platforms 
- IA32, IA64, Intel-64/X64
- Enables rapid development
- Contents of a driver:
- Entry Point
- Published Functions
- Consumed Functions
- Data Structures


- UEFI DRIVERS Follow  the UEFI Driver Model Specification  Sec 10 UEFI 2.X Spec
- Initialization
- Binding
	- Supported
	- Start
	- Stop
- Component name
- Configuration
- Diagnostic
- Driver Health
- Unload

---?image=/assets/images/slides/Slide12.JPG
<!-- .slide: data-transition="none" -->

@title[UEFI Boot Flow BDS]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>BDS</b> </span></p>


Note:
BDS<Br>
BDS is an Architectural Protocol gets dispatched from the DXE dispatcher.

Policy engine controls how the system will boot and has dependences on the Platform policy

BDS enumerates all possible boot devices in the system and create their boot option variables
 Current BDS will connect all devices and do this enumeration when user interrupts auto boot 
- Boot Manager & Device Manager
- Boot Maintenance Manager
- Current BDS has two steps to enumerate the boot option
- Legacy boot option for legacy boot (CSM)
- UEFI boot option for UEFI boot

- Globally Defined Variables
  -  BootOrder	ConIn
  -   BootNext		ConOut
  -   Boot####	ErrOut

- UEFI Device Path 
- An UEFI Device Path describes a boot target
- Binary description of the physical location of a specific target


+++?image=/assets/images/slides/Slide17_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow Device Path]
#### <p align="right"><span class="gold">UEFI Device Path and Global Variables</span>
<p style="line-height:80%" align="left"><span style="font-size:0.90em;" >
The UEFI Device Path describes a boot target <br>
&nbsp;&bull; &nbsp;@size[.70em;](Binary description of the physical location of a specific target)
</span></p>
```
   Acpi(PNP0A03,0) /Pci(1F|1) /Ata(Primary,Master) /HD(Part3, Sig010…) \EFI\Boot/OSLoader.efi

```

Note:
Device Path and Global Variables<Br>
The use of device paths allows the system resources to be defined in terms of connections between hardware devices, and the “pathways” the processor must follow to get to those devices.  

This includes the pathway to a specific boot device.

In the Example: 
The Boot target is the OS loader UEFI Application located on the third partition of the Master drive on the primary ATA controller off of the PCI Device 1Fh, function #1, off of the primary PCI host bridge (Bus zero).   This is how we would refer to this target, starting form the target working back to the processor, in UEFI, the target is defined starting from the processor, as devices are discovered and drivers are loaded in the boot process.  

Starting from the beginning, The initialization of the PCI Root Bridge is a one of the fundamental steps in system initialization,   Many hardware components are attached to the PCI bus, and this step is necessary to discover all subsequent devices on the PCI bus.  In the example, the PNP ID found is associated with the Root PCI device in the system (the Northbridge/Southbridge pair, or the equivalent).  This establishes the basis of PCI BUS zero and the root for additional PCI devices (and buses).

On PCI Bus zero, there exists (device 1Fh, Function 1) and IDE controller.  This device discovered and initialized by a driver to initialize PCI devices.  Note: this process is part of PCI initialization, it initialized the controller, but is not concerned with any “children” devices attached (downstream) to the controller, this will be handled later.

The devices on the IDE controller are now being initialized.  An ATA driver is associated with the drives, and the the Primary Master disk drive is now initialized.  

This occurs at the same time the system consoles are established (near boot device select timeframe).  This is important, as the HDD will not be initialize in the Pre-boot flow, unless it is the current “Targeted Boot Device” or the user has selected “Setup” as the boot path.

If the HDD is the Current targeted device, then it has to be initialized to be able to use for boot (obviously).  However, if the system does not need the device to attempt the boot, then it will not waste time initializing a device that is not necessary.

In the case of setup, the system is not ‘booting’ to an OS, but rather the user is configuring the systems options.  It is therefore necessary for all system options (hardware) to be initialized, so the user has a complete and accurate inventory to work with in the configuration process.

The drive was initialized in the last step, but drives may contain several partitions (in this case, the partition of interest is Partition 3), so a partition driver is associated to point to the proper partition on the drive.

The final stage in following the path, is to access the files on the target partition and load the Boot loader program.  

File access is handled by a File system driver, which has to be initialized for the drive and partition targeted (Primary Master ATA, Partition #3).  Once initialized, the file structure can be parsed, the the boot loader file (OSLoader.efi) can be loaded into memory and executed.  

This begins the launch of the OS, and the transition state for the boot firmware to the operating system.

However, now that the process is underway, there is still the software process of booting the OS.  The OS loader will ensure that the system is capable of booting the OS by running diagnostics (at least to ensure that the OS image on the disk is viable to boot an OS).  IF the diagnostics fail, the OS loader can return the system to the firmware, to allow it to attempt to boot from the next boot target in the list of ‘bootable devices”.

Assuming a complete and successful execution of Diagnostics, the OS loader will load the OS code, and the Boot process will complete as part of the OS’s function.

This Boot of the operating system was initiated, and successful, starting from a a simple path defining the device (location) from which to boot, and ending with a viable OS execution on the platfrom. 

---?image=/assets/images/slides/Slide14.JPG
<!-- .slide: data-transition="none" -->

@title[UEFI Boot Flow HII]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>HII</b> </span></p>


Note:
HII<Br>
UEFI Human Interface Infrastructure (HII)
System firmware has a common setup browser
Drivers don’t carry their own UI
Single point for pre-OS setup interface
Firmware & Drivers publish to a “database”

Components:
Strings are represented by string tokens.  They are listed in a table and referenced by a token number.  This results in multiple language support.  Depending the language, different tables are accessed.
Fonts
Presumption of bitmap fonts for easier localization
Keyboard
Keyboard Mapping
Forms
Describe user interface layout for ‘windowing’ interfaces
An application that uses String and Font support
Package
Self supporting data structure containing fonts, strings, and forms from a driver or set of drivers


Minimum FILES needed for HII 
.c - Driver source file  
Consumes HII protocols
Produces EFI_HII_CONFIGURATION_ACCESS_PROTOCOL
Publishes Forms Package
.h   Driver include file 
Defines configuration data
Defines private data 
.uni    Strings file 
Defines strings in different languages
.vfr    Forms file  
Defines the layout of the screen 
.inf    Pre-Make file 

+++?image=/assets/images/slides/Slide15.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
    
@title[UEFI Boot Flow HII- Simple]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>HII</b> </span></p>

Note:
HII<Br>
    Simple
+++?image=/assets/images/slides/Slide16.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow HII- Complex]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>HII</b> </span></p>

Note:
HII<Br>
    Complex

	
---?image=/assets/images/slides/Slide17.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow Shell]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>TSL</b> </span></p>



Note:
UEFI Shell<Br>
- UEFI Shell has complete control of the whole platform and resources
	
---?image=/assets/images/slides/Slide18.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow Boot Loader]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">-&nbsp;<b>Boot Loader</b> </span></p>


Note:
Boot Loader<Br>
- OS Boot Loader Application will call "Exit Boot Services"
	
+++?image=/assets/images/slides/Slide19.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow Boot Exit]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">-&nbsp;<b>Event</b> </span></p>

Note:

	
+++?image=/assets/images/slides/Slide20.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Flow Boot OS]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">-&nbsp;<b>Boot UEFI OS</b> </span></p>



Note:
Boot UEFI OS<Br>
TSL: 
- Pre –boot 
- Can run UEFI Applications and Drivers
- EFI System Table is available
- All of the system is available (I/O, Memory, PCI devices,  NV Ram, etc)
- Manufacturing Test Applications can run
- UEFI Shell 


Run Time

- Our Job is done

- When the OS takes over it can provide a virtual address space for the EFI Runtime Services. See UEFI 2.5 Chapter 7 Runtime Services - 7.4 Virtual Memory Services

---?image=/assets/images/slides/Slide21.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Legacy]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">-&nbsp;<b>Boot Legacy</b> </span></p>


Note:
Legacy boot with CSM<Br>

+++?image=/assets/images/slides/Slide22.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Boot Legacy no UEFI]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;-&nbsp;<b>Boot Legacy</b> </span></p>


Note:
Legacy boot with CSM<Br>
UEFI is not available until after a reset

---?image=assets/images/binary-strings-black2.jpg
@title[Intel FSP Section]
<br><br><br><br><br>
### <span class="gold"  >The Intel® Firmware Support Package (Intel® FSP) </span>

Note:
Section on Intel FSP
---
@title[Intel FSP Description]
<br>
#### <span class="gold">Intel® FSP  -  Components </span>
- CPU, memory controller, and chipset initialization functions as a binary package
- Provides silicon initialization ingredients
- Plugs into existing firmware frameworks
- Integration guide, includes API documentation

<p align="left" style="margin-top: -3px; margin-bottom: -3px"><span style="color:white; font-size:0.6em"> 
<br>
<BR>
<p style="line-height:70%"><span style="font-size:0.8em" >Intel FSP is currently available for the many Intel hardware-producing divisions &nbsp;&nbsp;&nbsp;
See: <a href="https://firmware.intel.com/learn/fsp/about-intel-fsp"> About Intel FSP</a> </span></p>
<p style="line-height:70%"><span style="font-size:0.8em" >White Paper Example: <a href="https://github.com/mangguo321/Braswell/blob/master/Documents/Open_Braswell_Platform_Designing_Porting_Guide.pdf">
Open Braswell - Design and Porting Guide</a></span></span></p>

Note:
The Intel® Firmware Support Package (Intel® FSP) is a royalty-free option for initializing Intel silicon, designed for integration into a boot loader of the developer's choice. It is easy to adopt, is scalable to design, reduces time to market, and is economical to build. Intel FSP provides a binary package to initialize the processor, memory controller, and Intel® chipset initialization functions.
Intel FSP is designed for integration into a variety of boot loaders, including coreboot and TianoCore (open source Unified Extensible Firmware Interface [UEFI]).


---?image=/assets/images/slides/Slide24.JPG
<!-- .slide: data-transition="none" -->
@title[Intel FSP Diagram-1]
#### <p align="center"><span class="gold">Intel® FSP to Open Source EDK II </span>


Note:
Intel FSP 1<Br>
+++?image=/assets/images/slides/Slide25.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Intel FSP Diagram-2]
#### <p align="center"><span class="gold">Intel® FSP to Open Source EDK II </span>
    


Note:
Intel FSP 2<Br>    

+++?image=/assets/images/slides/Slide26.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Intel FSP Diagram-3]

<p align="center" style="margin-top: -3px; margin-bottom: -3px"><span style="color:white; font-size:0.75em"> 
Intel®  FSP "Produced" to <br> "Consuming" Intel® Architecture Firmware </span>
 
Note:
Applying “Produced” Intel® Firmware Support Package (FSP) to “Consuming” IA firmware <Br>  

---?image=/assets/images/slides/Slide27.JPG
<!-- .slide: data-transition="none" -->

@title[Intel FSP from UEFI Boot Flow]
#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>FSP</b> </span></p>


Note:
Platform Initialization (PI) & UEFI w/ EDK <Br>
- Intel FSP boot flow   
 
+++?image=/assets/images/slides/Slide28.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Intel FSP from UEFI Boot Flow 2]

#### <p align="center"><span class="gold">UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>FSP</b> </span></p>

Note:
Platform Initialization (PI) & UEFI w/ EDK <Br>
- Intel FSP boot flow    


---
@title[Intel FSP Producer]
##### <p align="center"<span class="gold">Intel® FSP  - Producer </span></p>
<ul style="line-height:0.8;">
  <li><span style="font-size:0.8em" > Examples of binary instances on   <a href="http://www.intel.com/fsp">http://www.intel.com/fsp </a> with integration guides</span></li>
  <ul style="list-style-type:disc" style="line-height:0.8;" >
    <li><span style="font-size:0.67em" >This includes hardware initialization code that is EDK II based PEI Modules (PEIM’s)</span></li>
  </ul>
  <li><span style="font-size:0.8em" >Modules are encapsulated as a UEFI PI firmware volume w/ extra header</span></li>
  <li><span style="font-size:0.8em" >Configure w/Vital Product Data (VPD)-style Platform Configuration Data (PCD) externalized from the modules</span></li>
  <li><span style="font-size:0.8em" >Resultant output state reported via UEFI Platform Initialization (PI) Hand Off Block (HOB)</span></li>
</ul>
<p style="line-height:50%"><span style="font-size:0.5em" > <a href="http://www.intel.com/content/dam/www/public/us/en/documents/technical-specifications/fsp-architecture-spec-v2.pdf"> Intel® Firmware Support Package (Intel® FSP) External Architecture Specification (EAS) v2.0 PDF </a><BR>
 Resource: <a href="https://firmware.intel.com/blog/open-source-platforms-edkii-using-intel-fsp">https://firmware.intel.com/blog/open-source-platforms-edkii-using-intel-fsp  </a> </span> </p>

Note:

---
@title[Intel FSP Source]
##### <p align="right"><span class="gold">Source for Intel® FSP  Producer Code</span></p>

<ul style="line-height:0.8;">
  <li><span style="font-size:0.8em" >CPU and chipset-specific code for PEIM’s inside of the Intel FSP can be open or closed, added to… </span></li><br>
  <li><span style="font-size:0.8em" >PEI core and infrastructure code at <a href="https://github.com/tianocore/edk2"> tianocore.org/edk2 </a></span></li>
  <ul style="list-style-type:disc" style="line-height:0.8;" >
     <li><span style="font-size:0.7em" ><a href="https://github.com/tianocore/edk2/tree/master/MdePkg"> `/MdePkg` </a></span></li>
     <li><span style="font-size:0.7em" ><a href="https://github.com/tianocore/edk2/tree/master/MdeModulePkg"> `/MdeModulePkg` </a></span></li><br>
  </ul>
  <li><span style="font-size:0.8em" >And the code to create the Intel FSP interfaces can be found at</span></li> 
   <ul style="list-style-type:disc" style="line-height:0.8;" >
     <li><span style="font-size:0.7em" ><a href="https://github.com/tianocore/edk2/tree/master/IntelFsp2Pkg"> `/IntelFsp2Pkg` </a></span></li>
   </li>
<br>
<br>
@box[bg-purple text-white rounded fragment](Intel FSP can encapsulate IP protected initialization code PRODUCED by Intel business units) -

Note:

All of the public FSP’s are ‘EDK2-based’.   This package is the alignment of producing FSP’s going forward w/ aligned code.  This is the silicon reference code which is currently NDA – memory init PEIM + PCH init + uncore init.  It is a subset of the silicon pieces we have today.  Today’s RC is the superset.  Align customization over time.

Talking point – anyone would could be producer.  IBV could.  Just worry about quality/consistency.   Don’t put on a foil but have a position to respond to this.   FspPkg given to customers just like SI Rc.  NDA folks can do it.  OEM’s can do it.  OEM’s can produce it.  IBV + OEM are logical YES – under the SI code license NDA.   Platform SLA.


---?image=assets/images/binary-strings-black2.jpg  
@title[Whats New in UEFI Section]    
<br><br><br><br><br>
### <span class="gold"  >What's new in the UEFI Specifications  </span>



---?image=/assets/images/slides/Slide37_1.JPG
<!-- .slide: data-transition="none" -->

@title[UEFI Spec pic]    
#### <p align="center"><span class="gold">Latest UEFI Specifications </span> </p>
<p align="right"><span style="font-size:0.6em" ><a href="http://www.uefi.org"> http://uefi.org</a></span></p>

<br><br><br><br><br><br><br><br><br><br>
<p align="right"><span style="font-size:0.6em" ><a href="http://www.uefi.org/specsandtesttools"> http:///uefi.org/specsandtesttools </a>
</span></p>

Note:
- UEFI Specifications v2.7A (9/2017)
- ACPI Specification v6.2 (5/2017)
- UEFI Shell Specification v2.2 (1/2016)
- PI Packaging Specification v1.1 (1/2016)
- UEFI PI Specification v1.6 (5/2017)

---?image=/assets/images/slides/Slide35.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Spec Whats New] 
<br>   
<p align="right"><span class="gold">What's New in the UEFI Specifications </span> </p>
<br><br><br><br><br><br>
<p align="right"><span style="font-size:0.8em" > Resources Presented at Events from <a href="http://www.uefi.org/learning_center/presentationsandvideos/">
UEFI Forum Education Link </a></span></p>

Note:



---  
@title[UDK2018 Key Features]   
<br> 
<p align="center"><span style="color:#e49436; font-size: 1.0em"> UDK2018: Key Features - Q2 2018</span> </p>
<p align="Left"><span style="color:#e49436; font-size:0.8em"> UEFI Development Kit (UDK) releases are stable, validated snapshots of EDK II  </span> </p>
<div class="left">
     <ul style="list-style-type:disc; line-height:0.8;">
        <li><span style="font-size:0.7em">Industry Standards & Public Specifications</span> </li>
        <ul style="list-style-type:disc; line-height:0.8;">
          <li><span style="font-size:0.7em">UEFI 2.7</span></li>
          <li><span style="font-size:0.7em">UEFI PI 1.6</span></li>
          <li><span style="font-size:0.7em">ACPI 6.2</span></li>
        </ul>
        <li><span style="font-size:0.7em">Centralized Config Management </span></li>
        <li><span style="font-size:0.7em">IOMMU-based DMA Protection</span></li>
        <li><span style="font-size:0.7em">Stack Guard, Heap Guard and NULL Pointer Detection</span></li>
    </ul>
</div>
<div class="right">
    <ul style="list-style-type:disc; line-height:0.8;">
        <li><span style="font-size:0.7em">Compilers / Tools</span></li>
        <li><span style="font-size:0.7em">Microsoft Visual Studio 2017 tool chain</span></li>
        <li><span style="font-size:0.7em">Hash-based incremental build</span></li>
        <li><span style="font-size:0.7em">Build time improvement using multi-threading in GenFds to generate FFS files</span></li>
        <li><span style="font-size:0.7em">More Info: 
	<a href="https://github.com/tianocore/tianocore.github.io/wiki/UDK2018#edk-ii-specification-for-udk2018">TianoCore Wiki UDK2018 </a></span></li>
    </ul>
</div>

---  
@title[EDK II Community Development]   
<p align="center"><span class="gold"   >@size[1.1em](<b>EDK II - Open Source &nbsp;&nbsp;&nbsp; </b>)</span></p>
<br>

<span style="font-size:01.0em">@color[#e49436](Community Development)</span>
<div class="left1">
     <ul style="list-style-type:disc; line-height:0.8;">
        <li><span style="font-size:0.8em">Stable Tag Releases- cycle of releasing stable versions of  EDK II Firmware </span> </li>
        <li><span style="font-size:0.8em">Adding UEFI Spec updates and new key features  and bug fixes</span> </li>
        <li><span style="font-size:0.8em">Three phases of development</span> </li>
        <ul style="list-style-type:none; line-height:0.65;">
           <li><span style="font-size:0.65em">- Development phase</span> </li>
           <li><span style="font-size:0.65em">- Soft Feature Freeze</span> </li>
           <li><span style="font-size:0.65em">- Hard Feature Freeze</span> </li>
        </ul>
     </ul>
</div>
<div class="right1">
<span style="font-size:0.7em">&nbsp;</span>
</div>

@snap[north-east span-30 ]
<br>
<br>
![Logo](/assets/images/TianocoreLogo.png )
@snapend

@snap[north-east span-35 ]
<br><br><br><br>
![Community](/assets/images/Community.png )
@snapend

@snap[south-east span-45 ]
<p style="line-height:70%" align="left"><span style="font-size:0.7em">
Tag: edk2-stable201903 Features:<br>
&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/releases">	edk2 releases Stable tag</a><br>
<br>
</span></p>
@snapend

Note:

Clip art CC - https://carolahand.files.wordpress.com/2015/06/community-clipart-dt6xbagt9.png 

Stable Tag releases are validated snapshots of EDK II adding updates and new key features  and bug fixes


There is a development phase, 
Soft Feature Freeze
The soft feature freeze is the beginning of the stabilization phase of edk2's development process. By the date of the soft feature freeze, developers must have sent their patches to the mailing list andreceived positive maintainer reviews (Reviewed-by or Acked-by tags). This means that features, and in particular non-trivial ones, must have been accepted by maintainers before the soft freeze date.
Between the soft feature freeze and the hard feature freeze, previously reviewed and unit-tested features may be applied (or merged) to the master branch, for integration testing. Feature addition or enablement patches posted or reviewed after the soft feature freeze will be delayed until after the upcoming stable tag.


---  
@title[Summary]
##### <p align="center"<span class="gold"   >Summary </span></p><br>

 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Review PI and UEFI Boot Process  </span><br><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Answer <a href='https://github.com/tianocore/tianocore.github.io/wiki/UEFI%20EDKII%20Learning%20Dev'>web-based training</a> related questions </span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Answer: Where does Intel® FSP Fit?  </span> <br><br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;What’s new in UEFI.org </span> 



---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG =10x) 

---
@title[return to main]
<p align="center"><span class="gold"   >@size[1.2em](<b>Return to Main Training Page</b>)</span></p>
<br>
<br>
<br>
<br>
<br>
<p align="center"><span style="font-size:0.9em">Return to Training Table of contents for next presentation <a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">link</a></span></p>

@snap[north span-30 ]
<br>
<br>
<br>
<a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">
![trainingLogo](/assets/images/returnTrainingLogo.png)</a>
@snapend


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)

---  
@title[Backup]
<br><br><br><br><br>
### <p align="center"><span class="gold"   >Backup </span></p>

---
@title[FSP detail 1]
<p align="center"><span style="font-size:0.8em"><b>Intel® FSP V2.0 Boot Flow</b></span> </p>
![FSP-Detail-1](/assets/images/slides/bg48_1.jpg =10x) 
<p style="line-height:50%"><span style="font-size:0.5em"> Whitpaper:Using Intel® FSP with EDK II: <a href="https://firmware.intel.com/sites/default/files/A_Tour_Beyond_BIOS_Using_the_Intel_Firmware_Support_Package_with_the_EFI_Developer_Kit_II_(FSP2.0).pdf "> PDF</a>
<br></span> <span style="font-size:0.3em"> Intel® Firmware Support Package (Intel® FSP)   </span> </p>
	
Note:
The Intel® Firmware Support Package (Intel® FSP) [FSP] provides key programming information for initializing Intel silicon and can be easily integrated into a firmware boot environment of the developer’s choice. 
Different Intel hardware devices may have different Intel FSP binary instances, so a platform user needs to choose the right Intel FSP binary release. The FSP binary should be independent of the platform design but specific to the Intel CPU and chipset complex. We refer to the entities that create the FSP binary as the “FSP Producer” and the developer who integrates the FSP into some platform firmware as the “FSP Consumer.” 
Despite the variability of the FSP binaries, the FSP API caller (aka FSP consumer) could be a generic module to invoke the 5 APIs defined in FSP EAS (External Architecture Specification) to finish silicon initialization. [FSP EAS] 
The flow below describes the FSP, with the FSP binary from the “FSP Producer” in green and the platform code that integrates the binary, or the “FSP Consumer”, in blue. 

Source https://firmware.intel.com/sites/default/files/A_Tour_Beyond_BIOS_Using_the_Intel_Firmware_Support_Package_with_the_EFI_Developer_Kit_II_%28FSP2.0%29.pdf 

---
@title[FSP detail 2]
<p align="right" ><span style="font-size:0.75em">Diagram illustrates the high level boot flow</span>

![FSP-Detail-2](/assets/images/slides/bg42_1.jpg =10x) 

<span style="font-size:0.75em"> Image Source: Open Braswell Platform Desiging Porting Guide <a href="https://github.com/mangguo321/Braswell/raw/master/Documents/Open_Braswell_Platform_Designing_Porting_Guide.pdf 
	"> PDF </a></span>
Note:
Open Braswell EDKII FSP
Wrapper is responsible for communicating with Braswell FSP APIs in SEC, PEI, and
BDS phase
https://github.com/mangguo321/Braswell/raw/master/Documents/Open_Braswell_Platform_Designing_Porting_Guide.pdf 

---
@title[UEFI & EDK II Timeline]    
<p align="center"<span style="color:white; font-size:0.7em"> UEFI Specification & EDK II Reference Implementation Timeline  </span></p>
<p align="center"<span style="color:white; font-size:0.4em"> <a href="http://www.uefi.org/">UEFI Specification</a> -top &nbsp;&nbsp;&nbsp;&nbsp; & &nbsp;&nbsp;&nbsp;&nbsp;<a href="http://www.tiancore.org/">EDK II Open Source</a> -bottom </span></p>

![Timeline](/assets/images/slides/bg30.jpg) 
---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<BR><BR><BR>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)

---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2019, Intel Corporation. All rights reserved.
**/

```
