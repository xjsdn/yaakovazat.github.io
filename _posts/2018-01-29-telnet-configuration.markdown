---
layout:     post
title:      "An aggregate of Network Technologies's homeworks"
subtitle:   ""
date:       2018-01-29 01:05:00
author:     "Yaakov Azat"
header-img: "img/post-bg-universe.jpg"
---

# An aggregate of Network Technologies's homeworks

>An aggregate of Network Technologies's homeworks.Thanks for the help of [Маликова Ф.У.](http://www.kaznu.kz/)
> Full article and related sourcecode canbe found at [Github](https://github.com/yaakovazat/network-technology)

Some related sources:  
* [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatshe)  
* [Cisco Network Academy](https://www.netacad.com/)  
* [Cisco Paket Tracer](https://www.netacad.com/courses/packet-tracer-download/)  

## Telnet configiratin on Cisco Paket Tracer

The [Telnet](http://wikipedia.org/wiki/telnet) or "teletype network",is a protocol used on the Internet or local area networks to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection. 

[Telnet](https://zh.wikipedia.org/wiki/telnet)是Internet远程登录服务的标准协议和主要方式，常用于网页服务器的远程控制，可供用户在本地主机运行远程主机上的工作。

[TELNET](https://ru.wikipedia.org/wiki/telnet) (сокр. от англ. teletype network) — сетевой протокол для реализации текстового интерфейса по сети (в современной форме — при помощи транспорта TCP). 

### The basic topology of Telnet network testing is as follows:  
![topology](https://github.com/yaakovazat/network-technology/blob/master/01.png)
1. Use a c3560 switch and a host  
![](github.com/yaakovazat/network-technology/blob/master/01.png)
2. First configure the user name and password of c3560  
``` 
Switch#
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#user kaznu password yaakov
```  
3. Then configure the privileged password  
```
Switch(config)#enable password yaakov
```  
4. Next, configure the vty interface and log in using the local database user password.  
``` 
Switch(config)#line vty 0 4
Switch(config-line)#login local
```  
5. then
    * ip routing: Open the routing function of the three switches;
    * no switchport: switch off the switch port mode;
    * ip address 192.168.1.254 255.255.255.0: Configure the IP address of the interface;  
```
Switch(config-line)#ip routing
Switch(config)#int gigabitethernet 1/0/1
%Invalid interface type and number
Switch(config)#int fastethernet 0/1
Switch(config-if)#no switchport
Switch(config-if)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up

Switch(config-if)#ip add 192.168.1.254 255.255.255.0
Switch(config-if)#
```   
6. Then configure the PC.  
![configure pcip](https://github.com/yaakovazat/network-technology/blob/master/02.png)  
7. Then configure the PC's gateway
![gateway config](/03.png)  
8. Then call the PC cmd command line program
    * Enter the ``ipconfig / all`` command to view the configuration of the PC
    * ``Ping 192.168.1.254`` command, view the network connection
    * then Telnet Switch：``telnet 192.168.1.254``
    * Then enter the password and user name
    * Swith to Telnet successful !
![pc-cmd](/04.png)  

### Finally all i did step by step  
![telnet](https://github.com/yaakovazat/network-technology/blob/master/telnet1.gif)  
