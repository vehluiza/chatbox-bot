# chatbox-bot
from datetime import datetime

def responder(pergunta):
    pergunta = pergunta.lower()
    
    if "oi" in pergunta or "olá" in pergunta:
        return "Olá! Como posso te ajudar?"
    elif "nome" in pergunta:
        return "Eu sou um chatbot simples criado em Python."
    elif "hora" in pergunta:
        return "Agora são " + datetime.now().strftime("%H:%M")
    elif "ajuda" in pergunta:
        return "Claro! Você pode me perguntar sobre horário, meu nome, ou apenas conversar."
    elif "sair" in pergunta:
        return "Até logo!"
    else:
        return "Desculpe, não entendi. Pode repetir?"

# Execução principal
print("ChatBot iniciado! (Digite 'sair' para encerrar)")

with open("conversa.txt", "a", encoding="utf-8") as log:
    log.write("\n--- Nova conversa iniciada ---\n")
    while True:
        user_input = input("Você: ")
        resposta = responder(user_input)
        print("Bot: " + resposta)

        # Salvar no arquivo
        log.write(f"Você: {user_input}\n")
        log.write(f"Bot: {resposta}\n")

        if "sair" in user_input.lower():
            break
