# NFS-server

![nfs](https://user-images.githubusercontent.com/47100064/173202486-61cb9429-6675-48fe-aa9a-903e52f256ff.png)

NFS (Network file System) est un protocole qui permet de partager des répertoires et des fichiers avec d’autres clients Linux dans un réseau. 
Les répertoires à partager est généralement créé sur le serveur NFS et des fichiers y sont ajoutés.

Les systèmes clients montent le répertoire résidant sur le serveur NFS, ce qui leur donne accès aux fichiers créés. 
NFS est donc pratique pour partager des données communes entre les systèmes clients, en particulier lorsqu’ils manquent d’espace.

## INSTALLATION

- Mettre à jour les paquest d'installation

`sudo apt update`

- Installation

`sudo apt install nfs-kernel-server`

## CONFIGURATION

- Création d'un répertoire d’exportation (NFS Export Directory) 

`sudo mkdir -p /mnt/nfs_share`

- Supprimer tous restriction d'accès

`sudo mkdir -p /mnt/nfs_share`

- Autoriser l’accès au dossier partagé aux systèmes clients

`sudo nano /etc/exports`

- Pour accorder l’accès à un seul client, utilisez la commande suivante:

`/mnt/nfs_share  client_IP_1 (re,sync,no_subtree_check)`

- Pour plusieurs clients, il  faut indiquez chaque client un par un

`/mnt/nfs_share  client_IP_1 (re,sync,no_subtree_check)`

`/mnt/nfs_share  client_IP_2 (re,sync,no_subtree_check)`

- Exporté le fichier partagé

`sudo exportfs -a`

`sudo systemctl restart nfs-kernel-server`

- Autoriser le dossier partagé via le pare-feu

`sudo ufw allow from 192.168.43.0/24 to any port nfs`

`sudo ufw enable`

`sudo ufw status`

