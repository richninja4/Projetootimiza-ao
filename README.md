# Projetootimiza-ao
import tkinter as tk
from tkinter import messagebox

def calcular():
    try:
        # Dados da Cripto 1
        market_cap_1 = float(entry_market_cap_1.get())
        supply_1 = float(entry_supply_1.get())
        valor_1 = float(entry_valor_1.get())
        
        # Dados da Cripto 2
        market_cap_2 = float(entry_market_cap_2.get())
        supply_2 = float(entry_supply_2.get())
        valor_2 = float(entry_valor_2.get())

        # Calcula o preço teórico da Cripto 1 se tivesse o market cap da Cripto 2
        preco_comparativo = (market_cap_2 / supply_1)

        # Calcula valorização percentual
        variacao = ((preco_comparativo / valor_1) - 1) * 100

        # Exibe o resultado
        resultado_label.config(
            text=f"💰 Se {nome_cripto_1.get()} tivesse o Market Cap de {nome_cripto_2.get()},\n"
                 f"ela valeria aproximadamente: US$ {preco_comparativo:.4f}\n"
                 f"Variação: {variacao:.2f}%"
        )
    except ValueError:
        messagebox.showerror("Erro", "Por favor, insira apenas números válidos!")

# Criação da janela principal
janela = tk.Tk()
janela.title("Calculadora de Criptomoedas")
janela.geometry("500x500")
janela.configure(bg="#101820")

# Nome das criptos
tk.Label(janela, text="Cripto 1", bg="#101820", fg="#F2AA4C", font=("Arial", 12)).pack(pady=5)
nome_cripto_1 = tk.Entry(janela, font=("Arial", 12), justify="center")
nome_cripto_1.pack(pady=5)
tk.Label(janela, text="Market Cap (US$)", bg="#101820", fg="white").pack()
entry_market_cap_1 = tk.Entry(janela)
entry_market_cap_1.pack()
tk.Label(janela, text="Supply", bg="#101820", fg="white").pack()
entry_supply_1 = tk.Entry(janela)
entry_supply_1.pack()
tk.Label(janela, text="Valor atual (US$)", bg="#101820", fg="white").pack()
entry_valor_1 = tk.Entry(janela)
entry_valor_1.pack()

# Espaço entre as seções
tk.Label(janela, text=" ", bg="#101820").pack()

# Cripto 2
tk.Label(janela, text="Cripto 2 (para comparar)", bg="#101820", fg="#F2AA4C", font=("Arial", 12)).pack(pady=5)
nome_cripto_2 = tk.Entry(janela, font=("Arial", 12), justify="center")
nome_cripto_2.pack(pady=5)
tk.Label(janela, text="Market Cap (US$)", bg="#101820", fg="white").pack()
entry_market_cap_2 = tk.Entry(janela)
entry_market_cap_2.pack()
tk.Label(janela, text="Supply", bg="#101820", fg="white").pack()
entry_supply_2 = tk.Entry(janela)
entry_supply_2.pack()
tk.Label(janela, text="Valor atual (US$)", bg="#101820", fg="white").pack()
entry_valor_2 = tk.Entry(janela)
entry_valor_2.pack()

# Botão para calcular
tk.Button(janela, text="Comparar", command=calcular, bg="#F2AA4C", fg="black", font=("Arial", 12, "bold")).pack(pady=20)

# Resultado
resultado_label = tk.Label(janela, text="", bg="#101820", fg="white", font=("Arial", 11), justify="center")
resultado_label.pack(pady=10)

janela.mainloop()
