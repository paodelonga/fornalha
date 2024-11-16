---
date: 2024-10-09 05:40:02
title: Java Interfaces
tags: java, abstraction, polymorphism, object-oriented, programming, copy-only, translation
authors: paodelonga
---

# Interfaces

As interfaces se podem se parecer com as classes, mas existe uma diferença entre elas que é: uma _interface_ pode ter somente [assinatura de métodos]([[assinatura de métodos]]), campos e métodos padrão.

Em java uma interface é um [[tipos de referencia]], similar a uma [[classes]], ela contém apenas [[constantes]], [[assinatura de métodos]], [[métodos padrões]], [[métodos estáticos]] e [[tipos aninhados]].
O corpo de métodos existe apenas para os métodos padrões e estáticos. Diferentemente das classes uma interface não pode ser instanciada, MAS pode ser apenas _implementada_ por uma classe ou ser estendidas por outras interfaces. A extensão será discutida posteriormente nesta seção.

A definição de uma interface é similar a criação de uma classe:

```java
public inteface OperateCar {
	// Constant declarations, if any

	// Method signatures

	// An enum with values RIGHT, LEFT

	int turn(
		Direction direction,
		double radius,
		double startSpeed,
		double endSpeed
	);
	int changeLanes(
		Direction direction,
		double startSpeed,
		double endSpeed
	);
	int signalTurn(
		Direction direction,
		boolean signalOn
	);
	int getRadarFront(
		double distanceToCar,
		double speedOfCar
	);
	- [ ] int getRadarReac
		double distanceToCar,
		double speedOfCar
	)

	// .....
	// More method signature
}
```

Observe que na assinatura de métodos não é necessário a utilização de chaves, e o ponto e vírgula `;` é utilizado como caractere terminador.

Para utilizar uma interface, você deve escrever uma classe que implemente a interface. Quando uma classe instanciada implementa uma interface, ela provê um corpo do método para cada método declarado na interface. Por exemplo:

```java
public class OperateBMW760i implements OperateCar {
	// The OperateCar method signatures, with implementation --
	// for example:
	public int signalTurn(
		Direction direction,
		boolean signalOn
	); {
		// code to turn BMW's LEFT turn indicator lighsts on
		// code to turn BMW's LEFT turn indicator lighsts off
		// code to turn BMW's RIGHT turn indicator lighsts on
		// code to turn BMW's RIGHT turn indicator lighsts off
	}
	// other members, as needed -- for example, helper classes not
	// visible to clients of the interface
}
```

No exemplo acima, as fabricantes de automóveis que serão responsáveis pela implementação da interface. A implementação de um Chevrolet será substancialmente diferente da de um Toyota, é claro, mas ambas fabricantes irão aderir a mesma interface. Os fabricantes de orientação, que são clientes da interface, irão construir um sistema que utilize os dados de GPS na localização do carro, mapas digitais, e dados de tráfico para condução do carro, e quando feito, os sistemas de orientação invocarão os métodos da interface: girar, mudar de faixa, frear, acelerar, e assim por diante.

---
