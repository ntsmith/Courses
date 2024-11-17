FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y \
    build-essential git curl wget zlib1g-dev \
    ruby-full \
    ca-certificates software-properties-common \
    python3 python3-pip python3-dev python3-venv \
    && apt-get clean && rm -rf /var/lib/apt/lists/*
USER ubuntu

# Jekyll setup
ENV GEM_HOME="/home/ubuntu/gems"
ENV PATH="${GEM_HOME}/bin:${PATH}"
RUN gem install jekyll bundler && gem cleanup

# Python setup
ENV VIRTUAL_ENV=/home/ubuntu/venv
ENV PATH="${VIRTUAL_ENV}/bin:$PATH"
RUN python3 -m venv $VIRTUAL_ENV
RUN pip install --no-cache-dir \
    jupyter \
    notebook \
    jupyterlab \
    numpy \
    pandas \
    matplotlib \
    scipy \
    scikit-learn \
    seaborn \
    sympy \
    statsmodels \
    bokeh \
    plotly \
    ipywidgets \
    jupyter_contrib_nbextensions

# Configure Jupyter Notebook
# RUN jupyter notebook --generate-config && \
#     echo "c.NotebookApp.ip = '0.0.0.0'" >> /home/ubuntu/.jupyter/jupyter_notebook_config.py && \
#     echo "c.NotebookApp.allow_root = True" >> /home/ubuntu/.jupyter/jupyter_notebook_config.py && \
#     echo "c.NotebookApp.open_browser = False" >> /home/ubuntu/.jupyter/jupyter_notebook_config.py

# # Set the default command to run Jupyter Notebook
# CMD ["jupyter", "notebook", "--no-browser", "--ip=0.0.0.0", "--port=8888", "--allow-root"]

# Jekyll Port
EXPOSE 4000