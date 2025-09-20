# telegram.-auto.-reply.-bot
from telegram.ext import Updater, MessageHandler, Filters
import os

# Token Railway ke Environment Variable se lega
TOKEN = os.getenv("TOKEN")

def auto_reply(update, context):
    user_message = update.message.text.lower()

    if "hello" in user_message:
        reply_text = "Hello 👋"
    elif "good morning" in user_message:
        reply_text = "Good Morning ☀️"
    elif "love you" in user_message:
        reply_text = "Love you too ❤️"
    else:
        reply_text = None

    if reply_text:
        context.bot.send_message(chat_id=update.effective_chat.id, text=reply_text)

def main():
    updater = Updater(TOKEN, use_context=True)
    dp = updater.dispatcher
    dp.add_handler(MessageHandler(Filters.text & ~Filters.command, auto_reply))
    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()
    python-telegram-bot==13.15
    8473980257:AAFgM9qiBd5A4F5GDhbj2vh8SkJAyCwPYHM
