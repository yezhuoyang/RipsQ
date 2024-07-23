# RipsQ
This is the instructional repo for the rips project in UCLA. 


# Environment set up

The python version is 3.12.4. Please make sure that you have installed the latest pip and install all required package by:


```console
py -m pip install -r requirements.txt 
```

Please make sure that you can execute the jupyter notebook through your web browser or inside IDE like visual studio 



# Decomposing arbitrary unitary with qiskit

First, please install the latest version of qiskit by

```console
py -m pip install qiskit
```


Execute the following code in jupyter notebook:


```python
from qiskit import transpile
from qiskit import QuantumCircuit
from qiskit.quantum_info.operators import Operator


# Create a circuit with a register of two qubits
circ = QuantumCircuit(2)

#Unitary representation of gate you want to decompose
gate = Operator([
    [1, 0, 0, 0],
    [0, 0, 0, 1],
    [0, 0, 1, 0],
    [0, 1, 0, 0]
])


circ.unitary(gate, [0, 1], label='mygate')

#Gate set you want to use
target_basis = ['rz', 'h', 'cx']
decomposed = transpile(circ,
                       basis_gates=target_basis, 
                       optimization_level=0)  # 0 for no optimization, 3 is max



# Draw the circuit after decomposing
decomposed.draw('mpl')
```







