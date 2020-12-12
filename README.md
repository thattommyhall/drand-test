local:
ansible-playbook -i hosts drand-install.yml

Leader:
drand share --tls-disable --leader --nodes 20 --threshold 11 --secret-file /root/.drand/secret --period 30s

local:
ansible-playbook -i hosts initial-share.yml

leader:
drand share --tls-disable --leader --transition --nodes 25 --threshold 13 --secret-file /root/.drand/secret

copy group file into files/

ansible-playbook -i hosts reshare.yml
