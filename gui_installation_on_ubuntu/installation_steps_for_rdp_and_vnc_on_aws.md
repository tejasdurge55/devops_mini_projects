## VNC Installation Steps

![ubuntu_vnc_viewer](https://github.com/tejasdurge55/devops_mini_projects/blob/master/gui_installation_on_ubuntu/2025-03-21_10h24_38.png)

Create an ubuntu vm on aws with min 2vcpu having vnc port 5901 and ssh port 22 open in security group and insert the below commands:
```
sudo apt update
sudo apt install ubuntu-desktop
sudo apt install tightvncserver
sudo apt install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal
sudo apt install lxde
```

after the installation of ubuntu-desktop package, its possible that the further packages wont get installed

so we need to change nameserver
```
sudo vi /etc/resolv.conf
```

add namesever:
```
nameserver 8.8.8.8
```

again run the below commands, enter a password if it asks for it, you will require the password for logging in to vnc:
```
sudo apt install tightvncserver
sudo apt install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal
sudo apt install lxde
```
Configuring the VNC server:
```
vncserver :1
vim ~/.vnc/xstartup
```

press i and insert this at the last line:
```
/usr/bin/startlxde
```

save the file and run the below commands:
```
vncserver -kill :1
vncserver :1
```

open you vnc software and enter: `<aws-instace-public-ip>:1`

enter your password and you will be connected to the gui

right click ok the screen and change desktop appearance from black to other color for better visiblility


## RDP Installation Steps

![ubuntu_rdp](https://github.com/tejasdurge55/devops_mini_projects/blob/master/gui_installation_on_ubuntu/2025-03-21_10h52_32.png)

Create an ubuntu vm on aws with minimum 2vcpu having rdp port 3389 and ssh port 22 open in security group and insert the below commands:
```
sudo apt update
sudo apt install ubuntu-desktop
sudo apt install xrdp 
sudo systemctl status xrdp 
sudo adduser xrdp ssl-cert 
```

after the installation of ubuntu-desktop package, its possible that the further packages wont get installed

so we need to change nameserver
```
sudo vi /etc/resolv.conf
```

add namesever:
```
nameserver 8.8.8.8
```

again run the below commands, enter a password for root user, we require the password for logging in to rdp:
```
sudo su
sudo passwd
sudo apt install xrdp 
sudo systemctl status xrdp 
sudo adduser xrdp ssl-cert 
```

open the rdp client and type the instance ip and click on connect.

Then enter root and its password, you will be able to see the gui after logging in.
