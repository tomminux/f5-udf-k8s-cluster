# f5-udf-k8s-cluster

    cat ~/.ssh/id_rsa.pub

On each k8s cluster box (master and nodes) execute the following procedure

    echo "<put your public key here>" >> ~/.ssh/authorized_keys
    sudo su -
    echo "<put your public key here>" >> ~/.ssh/authorized_keys
    exit
    exit
   
On infra-server execute the following procedure:

    git clone https://github.com/tomminux/f5-udf-k8s-cluster.git
    vim ~/f5-udf-k8s-cluster/ansible/inventory/hosts
    cd ~/f5-udf-k8s-cluster/ansible/
    cp ~/registry.* ~/f5-udf-k8s-cluster/ansible/playbooks/files/docker-files/.
    ansible-playbook playbooks/install-k8s-cluster.yaml

On infra-server, create and modify the kubeconfig file

    bash ~/f5-udf-infra-server/init-scripts/3.create-kubeconfig.sh