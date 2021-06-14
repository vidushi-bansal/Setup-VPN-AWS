# Setting up a free VPN on AWS  
You need a VPN to keep yourself safe on the internet from the hackers, but you dont want to pay for it. We will setup a VPN server on aws cloud for free.  
[Prerequisites]  
AWS account  
  
1. Sign to the aws console at **aws.amazon.com**  
2. Click on **Services**  
3. Under compute, select **EC2**. EC2 is an Amazon service that will let us deploy a virtual machine in the cloud.  
4. Click on **Launch instances**.  
5. Select **AWS Marketplace** from the left bar. This will give some preconfigured tools that we require.
6. Type **Openvpn** in the textbox to search for relevant AMIs.  
![Openvpn_ami](https://github.com/vidushi-bansal/Setup-VPN-AWS/blob/main/openvpn_ami.png)  
This will be an Ubuntu server with Openvpn already installed.  
7. Click select.  
OpenVPN is a free and opensource software, but OpenVPN access server is a paid commercial option. Bring your own license (**BYOL**) gives us 2 clients for free.  
![BYOL](https://github.com/vidushi-bansal/Setup-VPN-AWS/blob/main/BYOL.png)    
8. Select continue.  
9. We are going to select **t2.micro** instance type.  
10. Click on the **Review and Launch** button from the bottom.  
11. Click on **Launch** and select your key-pair or create a new one.  
12. Finally, click on **Launch Instance**.  
13. Wait for your instance to get Ready.  
![Instance](https://github.com/vidushi-bansal/Setup-VPN-AWS/blob/main/Instance.png)  
14. Click on **connect** and copy the command and paste it in your terminal. Hit yes to accept the certificate.
15. Type yes to blindly accept the terms and conditions of the service.   
16. Configure the remaining opetions or to leave it as default just hit enter until it begins initializing openVPN.  
17. It will ask you to login as openvpnas user. Go ahead and do that.  
18. Now you will enter the server as ovenvpnas user. Type sudo passwd openvpn to change the password for the user openvpn. This is our admin user and our client user when we connect to our VPN portal.  
19. Type any password.  
20. Get back to aws console and copy the public ip.  
21. Open up a new tab and type https://Public-ip:943/admin  
![Openvpn_server](https://github.com/vidushi-bansal/Setup-VPN-AWS/blob/main/openvpn_server.png)  
22. Type the credentials. After clicking on Agree, you will be logged in to the activation manager page. 
![Activation_manager](https://github.com/vidushi-bansal/Setup-VPN-AWS/blob/main/activation_manager.png)  
23. Under configuration, go to the VPN settings. To make sure that all your internet traffic is safe and secure and going through this VPN, wherever you are, do the following:  
Under routing, select YES for Should client Internet traffic be routed through the VPN?  
![do_this](https://github.com/vidushi-bansal/Setup-VPN-AWS/blob/main/do_this.png)  
Scroll down and click Save Settings. Click on Update Running Server to make sure that the changes take place.  
**Setting up the server is completed here.**  
But, how are you going to connect to this VPN?
## Connecting to VPN  
Open a tab and type:   
https://Public-ip:943  
This will take you to the user portal. This is for clients or for the people who wants to connect. Use the same credentials.  
Now, choose the device you have and need to connect to the VPN from.  
Download the openvpn client for your system and intall it. Type in the credentials and you will be connected to the VPN. You can confirm this by checking what is my IP on google. It will display your openvpn server's public IP.  