# Guidelines how to start creating websites over IPFS

## What is IPFS
IPFS stands for Inter-planetary File System and it is a peer-to-peer mechanism to save and distribute files.

To quote the original explanation:
_*"A peer-to-peer hypermedia protocol
designed to preserve and grow humanity's knowledge
by making the web upgradeable, resilient, and more open."*_

You can learn more about it at the official website https://ipfs.io/ .

## Pre-requisities

### Local machine

We assume that you are working on the Ubuntu Linux distribution.

### Install IPFS CLI or IPFS Desktop

You can find complete guides about how to install a local IPFS node here:

- https://docs.ipfs.io/how-to/command-line-quick-start
- https://docs.ipfs.io/install/ipfs-desktop/

### Enable ports 4001,5001,8080 in your firewall

If you are using Ubuntu for development you can enable these port with ufw:

```
sudo ufw allow 4001
sudo ufw allow 5001
sudo ufw allow 8080
```

### Port-forwarding

In your router set the port 4001 to be forwarded in your local IPFS node either via static IP or MAC address.


## Steps to put your website to IPFS

### Create the content

Firstly, for the shake of this tutorial lets assume that you want to create a website with static content. You can of course use the files found in this repository.

*Create a folder named website*

Lets name this folder 'website'

*Create an index file*

You will need to create the main html file and name it as index.html 

*Add content in the file*

You can add the following content:

```
<!DOCTYPE html>
<html>
<meta charset="utf-8" />
<head>
    <title>First decentralized website</title>

    <style>
        body {
            margin: 15px;
            background-color: #fefefe;
            text-align:center;
        }
    </style>    

</head>

<body>
    <h1>Welcome to the decentralized web!</h1>
</body>
</html>
```

### Upload the content to IPFS

Please remember that you have to folder in your local node. You can do this via:

```
ipfs add -r website
```

This command will upload the folder and all its contents to IPFS. It will also give you back a hash of the folder.

### Pin your content

```
ipfs pin add -r /ipfs/<hash_of_website_folder>
```

With this command you ensure that your local node will keep the contents of the folder even it is not parsed regularly.

## View your content 

You can view your newly created one-page website via the official gateway ipfs.io like this:

https://ipfs.io/ipfs/<hash_of_website_folder>

You can also use the Cloudflares gateway likes this:
https://cloudflare-ipfs.com/ipfs/<hash_of_website_folder>

# Resources

- https://ipfs.io/
- https://developers.cloudflare.com/distributed-web/ipfs-gateway
