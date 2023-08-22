# rhods-gpu-testing
This is a repository providing sample code to test and verify that GPU's are available for your environment and also to run a small tensor based / CUDA based python program on GPUs.
Once you clone this repo on jypyterhub notebook after starting it on RHODS's environment using tensorflow based image, run the notebook `gpu-testing.ipynb` provided in this repo to test and verify GPU's.


Additonall, if you want you can download this git repo to have customized cuda based image to be used in RHODS.
git clone https://github.com/thinkahead/rhods-notebooks.git 
cd rhods-notebooks/interactive

podman build --format docker -f Dockerfile.gpu -t quay.io/thinkahead/notebooks:cuda-jupyter-minimal-ubi8-python-3.8-gpu . --tls-verify=false
podman push quay.io/thinkahead/notebooks:cuda-jupyter-minimal-ubi8-python-3.8-gpu

oc apply -f imagestream-gpu.yaml -n redhat-ods-applications
oc import-image cuda-a10gpu-notebook:cuda-jupyter-minimal-ubi8-python-3.8 -n redhat-ods-applications
oc import-image cuda-a10gpu-notebook:cuda-jupyter-minimal-ubi8-python-3.8-gpu -n redhat-ods-applications
