# UDPping
ping with UDP protocol 🛠

# How it looks like
```
root@raspberrypi:~# ./udpping.py 44.55.66.77 4000
UDPping 44.55.66.77 via port 4000 with 64 bytes of payload
Reply from 44.55.66.77 seq=0 time=138.357 ms
Reply from 44.55.66.77 seq=1 time=128.062 ms
Request timed out
Reply from 44.55.66.77 seq=3 time=136.370 ms
Reply from 44.55.66.77 seq=4 time=140.743 ms
Request timed out
Reply from 44.55.66.77 seq=6 time=143.438 ms
Reply from 44.55.66.77 seq=7 time=142.684 ms
Reply from 44.55.66.77 seq=8 time=138.871 ms
Reply from 44.55.66.77 seq=9 time=138.990 ms
^C
--- ping statistics ---
10 packets transmitted, 8 received, 20.00% packet loss
rtt min/avg/max = 128.06/138.44/143.44 ms
```

# Getting Started

### Step 1

Set up a udp echo server at the host you want to ping. 

There are many ways of doing this, my favourite way is:

```
socat -v UDP-LISTEN:4000,fork PIPE
```

Now a echo server is listening at port 4000. 

###### Note
If you dont have socat, use `apt install socat` or `yum install socat`, you will get it.

### Step 2

Ping you server.

Assume `44.55.66.77` is the IP of your server.

```
./udpping.py 44.55.66.77 4000
```

Done!

Now UDPping will generate outputs as a normal ping, but the protocol used is `UDP` instead of `ICMP`.

# Advanced Usage
```
root@raspberrypi:~# ./udpping.py
 usage:
   this_program <dest_ip> <dest_port>
   this_program <dest_ip> <dest_port> "<options>"

 options:
   LEN         the length of payload, unit:byte
   INTERVAL    the seconds waited between sending each packet, as well as the timeout for reply packet, unit: ms

 examples:
   ./udpping 44.55.66.77 4000
   ./udpping 44.55.66.77 4000 "LEN=400;INTERVAL=2000"
   
```
