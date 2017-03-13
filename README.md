# Server OS

Pretty simple idea. A web server, that runs on bare metal, has the necessary drivers, does what web servers do, could run node.js, doesn't run ON an operating system underneath, because it IS the operating system.

As a comparison, it is a bit like how (for example) chromeos is a web client that runs on bare metal in the form of a laptop, and can drive screens, keyboards, storage, network, etc. This would have an even simpler time - forget screens and keyboard, this only needs to run on raspberrypi or similar kinds of devices, and just needs to drive storage and network (and maybe blinkenlites).

As I say, you wouldn't install an operating system first then this server OS, you install this server OS, first, and perhaps stop there.

# context:
As a comparison, or a parallel, ChromeOS (the operating system of the Chromebook laptop product) is basically a browser - Chrome the browser. Normally you'd run Chrome or any other browser on top of an existing OS, such as macOS or Linux or whatever others there are out there on peoples computers.	  

The idea of the Chromebooks is that there's a good subset of people who only ever use their computer to go onto the web, so the only program they use is a web browser - the same browser each time - and they probably don't even realise it is known as a browser. They think that everything they see on the web is what the computer is showing them and that's what the computer is for. ChromeOS removes the superfluous underlying operating system, and all the other applications and programs on it, replacing it with only a browser, but one that can run on a computer directly as opposed to on top of an operating system.	  

The purpose of an operating system is to 'host' the running of a program. If it turns out to be the same program each time, arguably, there's no need for an operating system at all, except that the program by itself is insufficient to show evidence that it is actually doing anything - it can't drive the screen or listen for the keyboard or mouse, it can't access storage, it might be able to respond to the network but it doesn't know where the network hardware is nor what to do to make it work, etc. The operating system does that, normally. It runs a kernel - a program which basically starts when the computer starts and proceeds to run a recursing list of stuff that has to happen in the correct order, but with an eye to letting priority things interrupt when necessary, or slow things get pushed aside if it can be afforded. On the end of these list items are usually some end result tied to the machine itself - the physical keyboard electronics and mouse electronics (or as a protocol over USB these days), the screen display hardware, the network physical layer (PHY), any actual buttons, sensors, lights, any form of input/output, disk drives, beeping things, etc. All of those need drivers. The kernel runs the list of stuff to do, and calls the drivers to allow it to get input or output to or from the hardware. The drivers are each separate bits of code. The kernel doesn't need to be aware what is in each block of code, it just issues a standardised system call to the driver, the driver knows how to accept or give back useful results over agreed system calls that the kernel will be expecting.	  

In the current case of a web server, it'll most likely only ever run that web server application or program, but has to have a full operating system installed first, to host it - pretty much always these days. What this idea is suggesting is that a web server be given the magical powers to directly address hardware drivers (ie, working at the bare metal, rather than the abstraction layer of the OS and the limited set of application system calls it is allowed to communicate through while the kernel runs the whole show). If only the application could directly address device drivers (which is not the normal case), it wouldn't need a whole OS, and in the special case of a web server, it hardly needs a lot of drivers at all - just storage and network, unlike something like ChromeOS which needs to be a web browser that can by itself also draw the screen image, listen for mouse and keyboard activity, listen for network and put stuff out to the network physical layer, actually bundle data up and put it on disk and get it back, and do a lot of things with battery and power management along the way.	  

The bare metal bit suggests that you can't get any more fundamental in a computer - there's no layer or abstraction in between.
—	Ian Tindale, Mar 08 2017

# developmental strategy

very much a case of 

1. collect underpants
2. ?
3. launch Server OS

# refinements in direction

It could be entirely possible that this could be a node.js thing. Get node.js to be able to drive machine drivers, and get the other end of node.js to be able to run nginx. Then install it on something - bare metal, no other OS.
